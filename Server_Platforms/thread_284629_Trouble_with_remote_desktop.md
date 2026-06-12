---
title: "Trouble with remote desktop"
date: 2006-10-25
forum: Server Platforms
---

### Post by jvernon on 2006-10-25
I'm trying to remotely connect to my ubuntu (dapper) box from my windows XP box on the same network.  I tried the instructions here: [http://www.ubuntuforums.org/showthread.php?t=122402%20](http://www.ubuntuforums.org/showthread.php?t=122402%20)

When I test it by trying to connect with vncviewer I get a window with nothing but static.  Here is the command line output:

jeff@jeff-ubuntu:~$ vncviewer localhost:1
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.8 (viewer 3.3)
Password:
VNC authentication succeeded
Desktop name "x11"
Connected to VNC server, using protocol version 3.3
VNC server default format:
  16 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 31 green 63 blue 31, shift red 11 green 5 blue 0
Using default colormap and visual, TrueColor, depth 24.
Got 256 exact BGR233 colours out of 256
Using BGR233 pixel format:
  8 bits per pixel.
  True colour: max red 7 green 7 blue 3, shift red 0 green 3 blue 6

I couldn't figure out how to enable xdmcp, it is not on the security tab of gdmsetup.  Is that my problem?

I'm pretty new at this and would really appreciate the help.

---

### Post by jvernon on 2006-10-26
Ahhh, I just figured out that i need to use localhost:0 instead of :1.  It seems to work now and I get to feel like a big idiot.  Any reason why the instructions listed in my previous post said to use :1 ?

---

