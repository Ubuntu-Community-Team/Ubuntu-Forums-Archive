---
title: "Writing AppIndicator"
date: 2014-11-22
forum: Ubuntu Application Development
---

### Post by bashphoenux on 2014-11-22
Hi everyone,

Returned to Ubuntu after using Archlinux for quiet sometime now. 
I wanted to know if there are any good resources for appindicator development. I googled but couldn't find that many good tutorials/api page for AppIndicator.
So what I am trying to do is I have a note script for creating notes. I want to create an appindicator that would basically list all notes on a directory and when I click on the note open the note with vim.
Firstly I would like to know if this is feasible using AppIndicator ? If so I would like to know if there good resources to start development on it.
Thanks

---

### Post by osmoma on 2014-11-30
[FONT=arial narrow][FONT=arial]Hello,

EDIT: Pardon. Are you are using Python?

1) Install package [/FONT][/FONT][COLOR=#0060B0][FONT=UbuntuBeta Mono]**libappindicator3-dev**[/FONT][/COLOR][FONT=arial narrow][FONT=arial]
[/FONT][/FONT][FONT=arial narrow][FONT=arial]
2) Take a look at Audio-recorder. It has a systray module that supports both the older GNOME 2.x and the modern AppIndicator type indicators.
Please see: [http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/systray-icon.c](http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/systray-icon.c)

The code is rather old now, but it should give you some info.

You probably just want the parts from line 349#....and the general parts above it.
[COLOR=#507090]#ifdef HAS_APP_INDICATOR
...
...
[/COLOR]#endif 

Check also [COLOR=#000000]APP_INDICATOR_CFLAG and [/COLOR][COLOR=#000000]APP_INDICATOR_LIBS variables in configure.ac for Compiling and Linking. Or do
[/COLOR]$ pkg-config --libs appindicator3-0.1 
$ pkg-config --cflags appindicator3-0.1 

You may have different version of [/FONT][/FONT][FONT=arial] appindicator3.[/FONT][FONT=arial narrow][FONT=arial]

[/FONT]The A.R:
[/FONT][URL="https://launchpad.net/audio-recorder"]https://launchpad.net/audio-recorder
[/URL]
[COLOR=#000000][FONT=UbuntuBeta Mono]
[/FONT][/COLOR]

---

