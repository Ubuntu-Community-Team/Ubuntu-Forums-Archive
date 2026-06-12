---
title: "VNC server problems"
date: 2012-03-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by blm14 on 2012-03-09
I just installed 12.04 on a new machine, and I am having some trouble getting VNC to work. I should note that I did install gnome shell first.

I SSH to the box, issue either of the following two commands:

```

vnc4server -geometry 1280x720

```

or

```

vncserver -geometry 1280x720

```

In either case, I get output similar to this:

```

New 'fs-new:1 (ben)' desktop is fs-new:1

Starting applications specified in /home/ben/.vnc/xstartup
Log file is /home/ben/.vnc/fs-new:1.log

```

But then I go to another machine and attempt to connect (tightVNC client, windows 7 64bit), the connection succeeds and I see the default ubuntu background, but nothing else. No menus, no nav bars, nada.

Here is the output of ~/.vnc/fs-new:1.log from a brand new session, start to finish:

```

09/03/12 09:37:46 Xvnc version TightVNC-1.3.9
09/03/12 09:37:46 Copyright (C) 2000-2007 TightVNC Group
09/03/12 09:37:46 Copyright (C) 1999 AT&T Laboratories Cambridge
09/03/12 09:37:46 All Rights Reserved.
09/03/12 09:37:46 See http://www.tightvnc.com/ for information on TightVNC
09/03/12 09:37:46 Desktop name 'X' (fs-new:1)
09/03/12 09:37:46 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
09/03/12 09:37:46 Listening for VNC connections on TCP port 5901
Font directory '/usr/share/fonts/X11/75dpi/' not found - ignoring
Font directory '/usr/share/fonts/X11/100dpi/' not found - ignoring
xrdb: No such file or directory
xrdb: can't open file '/home/ben/.Xresources'

09/03/12 09:37:50 Got connection from client 192.168.1.6
09/03/12 09:37:50 Using protocol version 3.8
09/03/12 09:37:50 Enabling TightVNC protocol extensions
09/03/12 09:37:51 Full-control authentication passed by 192.168.1.6
09/03/12 09:37:51 Pixel format for client 192.168.1.6:
09/03/12 09:37:51   32 bpp, depth 24, little endian
09/03/12 09:37:51   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
09/03/12 09:37:51   no translation needed
09/03/12 09:37:51 Using tight encoding for client 192.168.1.6
09/03/12 09:37:51 rfbProcessClientNormalMessage: ignoring unknown encoding 8
09/03/12 09:37:51 Enabling X-style cursor updates for client 192.168.1.6
09/03/12 09:37:51 Enabling cursor position updates for client 192.168.1.6
09/03/12 09:37:51 Using image quality level 6 for client 192.168.1.6
09/03/12 09:37:51 Enabling LastRect protocol extension for client 192.168.1.6
09/03/12 09:37:51 rfbProcessClientNormalMessage: ignoring unknown encoding -223

```

has anyone succeeded in getting any VNC working on precise? Thanks!

---

