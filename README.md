# Sublime CodeMap

A plugin for displaying the code map (code structure tree) in the [Sublime Text 3](http://sublimetext.com "Sublime Text") editor.

This plugin is a port of [PyMap](https://marketplace.visualstudio.com/items?itemName=OlegShilo.PyMap) Visual Studio extension. 

Plugin currently supports building the code tree for Python. Support for C# is in the pipeline. The design of plugin allows integration of the user defined _tree building_ algorithm for other languages. The _custom syntax_ integration infrastructure and and samples will  be available in the next release. 

## Installation

Note the plugin was developed and tested against ST3 but not ST2.

*__Package Control__*

Currently the pluging is being evaluated by the Package Control team and it is expected to become available  via Package Control very soon. 

*__Manual__*

* Remove the package, if installed, using Package Control.
* Add a repository: `https://github.com/oleg-shilo/sublime-codemap.git`
* Install `sublime-codemap` with Package Control. 
* Restart Sublime editor if required

You can also install the plugin by cloning `sublime-codemap` repository into your Packages folder or manually placing the download package there.

## Usage
The plugin uses a dedicated view group __Code - Map__ (on right side) to mimic a "side bar" with the content (code tree) that represents code structure of the active view content in the primary view group. 

The code tree automatically refreshes on saving the active document or switching the tabs. The usage is quite simple. You can double-click a node in the code tree and this will trigger navigation to the corresponding area in the code (in active document). Alternatively you can synchronize code tree node selection with the current caret position in the document by triggering `sync_code_map` command either from _Command Palette_ or by the configured shortcut.

To start working with CodeMap just make the map view visible (e.g. [alt+m, alt+m]) and set the focus to the code view.

![](images/image1.gif)

## Command Palette

Press `cmd+shift+p`. Type `codemap` to see the available commands:

* *Toggle Visibility* - Show/Hide CodeMap view.
* *Reveal in CodeMap* - Select code tree node that corresponds the caret position in the code (active view)

## Custom mapping

You can extend the built-in functionality with custom mappers. Custom mapper is a Python script, which defines a mandatory `def generate(file)` routine that analyses a given file content and produces a 'code map' representing the content structure. 

You can find the [code_map.txt.py](custom_mappers/code_map.txt.py) sample in the source code. This mapper builds the list of paragraphs (new lines) in the given text file.
In order to activate the mapper its script meeds to be mapped to the supported file type (extension) in the *.sublime-settings file:
`"codemap_<extension>_mapper": "<path to the script implementing the mapper>"`

  Example: `"codemap_txt_mapper": "c:/st3/plugins/codemap/custom_mappers/code_map.txt.py"`
   

## Settings
Currently there is no any settings for the plugin except `codemap_<extension>_mapper` described in the section above.
