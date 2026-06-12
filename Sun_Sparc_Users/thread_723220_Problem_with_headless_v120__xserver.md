---
title: "Problem with headless v120 / xserver"
date: 2008-03-13
forum: Sun Sparc Users
---

### Post by malibu on 2008-03-13
Hi there, does anyone have experience installing VNC on a headless system?  I have built the current tightvnc but when I try to start vncserver it doesn't start.  When I try to start Xvnc directly I get the following:
$ Xvnc -geometry 1024x768
Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
13/03/08 09:15:53 Xvnc version TightVNC-1.3.9
13/03/08 09:15:53 Copyright (C) 2000-2007 TightVNC Group
13/03/08 09:15:53 Copyright (C) 1999 AT&T Laboratories Cambridge
13/03/08 09:15:53 All Rights Reserved.
13/03/08 09:15:53 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
13/03/08 09:15:53 Desktop name 'x11' (viper:0)
13/03/08 09:15:53 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
13/03/08 09:15:53 Listening for VNC connections on TCP port 5900
Font directory '/usr/X11R6/lib/X11/fonts/misc/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Type1/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/75dpi/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/100dpi/' not found - ignoring

Fatal server error:
could not open default font 'fixed'


When I try to install the fonts I get this:
$ apt-get install xfonts-base
......
......
FATAL: Module battery not found.
Unpacking replacement xfonts-base ...
FATAL: Module battery not found.
warning: /usr/lib/X11/fonts/misc does not exist or is not a directory
warning: /usr/lib/X11/fonts/misc does not exist or is not a directory
Setting up xfonts-base (1:1.0.0-4) ...
FATAL: Module battery not found.
warning: /usr/lib/X11/fonts/misc does not exist or is not a directory
warning: /usr/lib/X11/fonts/misc does not exist or is not a directory


Can anyone help me out with this?

---

