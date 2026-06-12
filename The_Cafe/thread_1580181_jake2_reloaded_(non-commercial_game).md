---
title: "jake2 reloaded (non-commercial game)"
date: 2010-09-23
forum: The Cafe
---

### Post by osmanpub on 2010-09-23
I've updated the original java port of quake2 to work with jdk 5/6. You can download it from:

[http://code.google.com/p/jake2-ext/downloads/list](http://code.google.com/p/jake2-ext/downloads/list)

Here is the quick start notes:

----------
Game Files
----------

If you have a legal copy or demo of the game, place the data in a folder
called jake2 in your home directory, e.g. /home/osman/jake2

You can download demo files from here for example:

[http://download.cnet.com/Quake-II-demo/3000-7563_4-10243474.html](http://download.cnet.com/Quake-II-demo/3000-7563_4-10243474.html)


------------
Running Game
------------

To run the game under linux, go to the scripts folder and type:

all:    sh 0.9.7.sh (recommended)

If for some reason you need to try JOAL/JOGL before LWJGL, use:

i586:   sh 0.9.6.sh 
amd64:  sh 0.9.6-64.sh 

On the first time, locate your data using the dialog box (ignore the download 
option). Subsequent runs should pick up the location from settings in a .jake2
folder in your home directory, e.g. /home/osman/.jake2

Experiment with adding cheats and commands in .jake2/config.cfg file to load
custom settings at start up.

=========================

You may need to install wine and a jre or jdk first.

---

