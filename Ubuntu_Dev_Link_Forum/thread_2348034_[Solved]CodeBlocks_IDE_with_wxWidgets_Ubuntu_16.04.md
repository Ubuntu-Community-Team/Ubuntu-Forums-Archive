---
title: "[Solved]CodeBlocks IDE with wxWidgets Ubuntu 16.04 64 Bit"
date: 2016-12-30
forum: Ubuntu Dev Link Forum
---

### Post by Floppyjoe on 2016-12-30
[IMG]https://3.bp.blogspot.com/-T8BTcv1SYdA/WGcX4VcHu4I/AAAAAAAAAHE/HpzG30ecrMgyQ9jlduQyvq7VeeGpOcwCgCLcB/s1600/wxWidgets1.png[/IMG]
The above picture is from Windows with the resulting error. I get another error after this one saying the release version won't build either.

I have been trying to install CodeBlocks IDE with the wxWidgets plugin on Windows 10 and on Ubuntu Linux 16.04 LTS 64 bit version.
[IMG]https://3.bp.blogspot.com/-k1FFcSeZS8k/WGcn0vV8L7I/AAAAAAAAAHY/SFFwXRb7ERQwEX7SbF5x21C_Bi5wyCE3ACLcB/s1600/Screenshot%2Bfrom%2B2016-12-30%2B21-31-39.png[/IMG]
While I have been able to install the IDE with ease there are problems of the program crashing when I install the codeblocks-contrib plugins package in Ubuntu Linux.

In Windows 10 I can't find any solution on how to install the wxWidgets and get it to work with the CodeBlocks IDE. There is no easy Howto that explains how
to get them to work together. In Windows I use the latest release of Codeblocks and the latest stable release of wxWidgets.

So far I have only been able to get it to work in the Windows 10 Subsystem for Linux Bash using the Xming x window system as a viewer. On my system this is Ubuntu
Linux 14.04 LTS 64 bit version.

This is the output when I run codeblocks from the command line:
> :~$ codeblocks
Initialize EditColourSet .....
Initialize EditColourSet: done.
Loading menubar...
Abbreviations: loaded
ThreadSearch: loaded
SmartIndentPython: loaded
CodeSnippets: loaded
SmartIndentLua: loaded
RegExTestbed: loaded
Exporter: loaded
EditorTweaks: loaded
AStylePlugin: loaded
wxSmith: loaded
wxSmithMime: loaded
AutoVersioning: loaded
wxSmithContribItems: loaded
BYOGames: loaded
Debugger: loaded
Compiler: loaded
DoxyBlocks: loaded
NassiShneidermanPlugin: loaded
BrowseTracker: loaded
ScriptedWizard: loaded
Profiler: loaded
MouseSap: loaded
SmartIndentFortran: loaded
FileManager: loaded
ProjectsImporter: loaded
OpenFilesList: loaded
OccurrencesHighlighting: loaded
CppCheck: loaded
ReopenEditor: loaded
cbDragScroll: loaded
SmartIndentCpp: loaded
CB_Koders: loaded
Valgrind: loaded
FilesExtensionHandler: loaded
HexEditor: loaded
EnvVars: loaded
SymTab: loaded
Cccc: loaded
CodeStat: loaded
Cscope: loaded
ToDoList: loaded
ClassWizard: loaded
EditorConfig: loaded
HeaderFixup: loaded
HelpPlugin: loaded
SmartIndentXML: loaded
lib_finder: loaded
SmartIndentPascal: loaded
copystrings: loaded
IncrementalSearch: loaded
ToolsPlus: loaded
SmartIndentHDL: loaded
SpellChecker: loaded
CodeCompletion: loaded
cbKeyBinder: loaded
Autosave: loaded
wxSmithAui: loaded
Abbreviations plugin activated
ThreadSearch plugin activated
SmartIndentPython plugin activated
Code snippets plugin activated
SmartIndentLua plugin activated
Regular expressions testbed plugin activated
Source Exporter plugin activated
Editor Tweaks plugin: Building menu
Editor Tweaks plugin: making the menu 15
Editor Tweaks plugin: Folding menu
EditorTweaks plugin activated
Source code formatter (AStyle) plugin activated
wxSmith plugin activated
wxSmith - MIME plugin plugin activated
AutoVersioning plugin activated
wxSmith - Contrib Items plugin activated
BYO Games plugin activated
Debugger plugin activated
Added compiler "GNU GCC Compiler"
Added compiler "Intel C/C++ Compiler"
Added compiler "GDC D Compiler"
Added compiler "GNU Fortran Compiler"
Added compiler "G95 Fortran Compiler"
Added compiler "GNU GCC Compiler for ARM"
Added compiler "GNU GCC Compiler for AVR"
Added compiler "Tiny C Compiler"
Added compiler "*No Compiler*"
Added compiler "LLVM Clang Compiler"
Added compiler "GNU GCC Compiler for PowerPC"
Added compiler "LLVM D Compiler"
Added compiler "GNU GCC Compiler for TriCore"
Added compiler "Digital Mars D Compiler"
Added compiler "GNU GCC Compiler for MSP430"
Added compiler "PGI Fortran Compiler"
Added compiler "Small Device C Compiler"
Compiler plugin activated
DoxyBlocks plugin activated
NassiShneidermanPlugin plugin activated
BrowseTracker plugin activated
Project wizard added for 'Empty project'
Project wizard added for 'Fortran application'
Project wizard added for 'Fortran library'
Project wizard added for 'Fortran DLL'
Project wizard added for 'Console application'
Project wizard added for 'D application'
Project wizard added for 'FLTK project'
Project wizard added for 'GLFW project'
Project wizard added for 'GLUT project'
Project wizard added for 'GTK+ project'
Project wizard added for 'Irrlicht project'
Project wizard added for 'Lightfeather project'
Project wizard added for 'Matlab project'
Project wizard added for 'OpenCV project'
Project wizard added for 'OpenGL project'
Project wizard added for 'Ogre project'
Project wizard added for 'Code::Blocks plugin'
Project wizard added for 'QT4 project'
Project wizard added for 'SDL project'
Project wizard added for 'SFML project'
Project wizard added for 'Static library'
Project wizard added for 'Shared library'
Project wizard added for 'wxWidgets project'
Build-target wizard added for 'Console'
Build-target wizard added for 'Static library'
Build-target wizard added for 'wxWidgets'
Project wizard added for 'ARM Project'
Project wizard added for 'AVR Project'
Project wizard added for 'TriCore Project'
Project wizard added for 'PowerPC Project'
Project wizard added for 'MCS51 Project'
File(s) wizard added for 'Empty file'
File(s) wizard added for 'C/C++ source'
File(s) wizard added for 'C/C++ header'
File(s) wizard added for 'Fortran source'
Scripted wizard plugin activated
Code profiler plugin activated
MouseSap plugin activated
SmartIndentFortran plugin activated
FileManager plugin activated
Foreign projects importer plugin activated
Open files list plugin activated
OccurrencesHighlighting plugin activated
CppCheck plugin activated
ReopenEditor plugin activated
DragScroll plugin activated
SmartIndentCpp plugin activated
Koders query plugin activated
Valgrind plugin activated
Files extension handler plugin activated
HexEditor plugin activated
Environment variables plugin activated
Symbol Table Plugin plugin activated
Cccc plugin activated
Code statistics plugin activated
Cscope plugin activated
Todo List plugin activated
Class wizard plugin activated
EditorConfig plugin for Code::Blocks plugin activated
Header Fixup plugin activated
Help plugin plugin activated
SmartIndentXML plugin activated
Segmentation fault (core dumped)


Any suggestions on how to get the programs to work on either system(Windows 10 64 bit/Ubuntu Linux 16.04 LTS 64 bit)? I am trying to learn the basics of developing a program with a GUI.

---

### Post by Floppyjoe on 2017-01-01
I found a solution on this link: [http://www.codeblocks.org/downloads/26#linux64](http://www.codeblocks.org/downloads/26#linux64)

I had to go to this link :[https://launchpad.net/~damien-moore/+archive/ubuntu/codeblocks-stable](https://launchpad.net/~damien-moore/+archive/ubuntu/codeblocks-stable)
and follow the directions to add a new repository to download an upgraded version of codeblocks and codeblocks-contrib.

It would be nice if Ubuntu would update their packages to ones which actually work together. I hope this post will help someone else searching for this answer.

Also to get it to work using precompiled binaries in Windows 10 you need to follow this very vague tutorial: [http://wiki.codeblocks.org/index.php/Using_wxWidgets_(MSW)_3.0_Binary_with_Code::Blocks_Scripted_Wizard](http://wiki.codeblocks.org/index.php/Using_wxWidgets_(MSW)_3.0_Binary_with_Code::Blocks_Scripted_Wizard)

---

