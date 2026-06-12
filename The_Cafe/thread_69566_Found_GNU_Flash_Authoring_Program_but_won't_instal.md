---
title: "Found: GNU Flash Authoring Program but won't install."
date: 2005-09-27
forum: The Cafe
---

### Post by Arktis on 2005-09-27
[http://f4l.sourceforge.net/]("http://f4l.sourceforge.net/")

We need to get this running on ubuntu.

```
arktis@arkhome:~/dloads$ sudo dpkg -i f4l_0.2-1_i386.deb
Selecting previously deselected package f4l.
(Reading database ... 90199 files and directories currently installed.)
Unpacking f4l (from f4l_0.2-1_i386.deb) ...
dpkg: dependency problems prevent configuration of f4l:
 f4l depends on libqt3c102-mt (>= 3:3.3.4); however:
  Package libqt3c102-mt is not installed.
 f4l depends on libqt3c102-mt (>= 3:3.3.4-3); however:
  Package libqt3c102-mt is not installed.
 f4l depends on libxrender1 (>= 1:0.9.0-2); however:
  Version of libxrender1 on system is 1:0.9.0-1.
dpkg: error processing f4l (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 f4l
``` libqt3c102-mt.... dear god, not THAT problem again; I run into this specific dependancy problem a lot. This is one thing that bugs me about ubuntu. libxrender is also a problem... meh.
```
arktis@arkhome:~/src/f4l-0.2$ make
make: *** No rule to make target `/mkspecs/default/qmake.conf', needed by `Makefile'.  Stop.
``` I have no idea what to do about that. If someone can get this running on breezy, then we can start testing this to see if it is a viable *native linux* alternative for creating flash.

---

### Post by tomwell on 2005-12-06
hey you should check out this post...

[http://www.ubuntuforums.org/showthread.php?t=91471&highlight=f4l](http://www.ubuntuforums.org/showthread.php?t=91471&highlight=f4l)

Peace

Tom

---

### Post by ssam on 2005-12-06
the future is animated SVG. well maybe.

---

