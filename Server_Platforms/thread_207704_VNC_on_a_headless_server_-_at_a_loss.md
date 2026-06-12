---
title: "VNC on a headless server - at a loss"
date: 2006-07-02
forum: Server Platforms
---

### Post by hagen00 on 2006-07-02
Hi, 

We did a fresh install of Dapper Server and I am trying to get VNC up and running. What worked before for me (on a debian sarge) was doing this:

```
apt-get install tightvncserver

apt-get install xfonts-base xfonts-75dpi xfonts-100dpi

vi /etc/vnc.conf and change line to
$fontPath = “/usr/lib/X11/fonts/75dpi/,/usr/lib/X11/fonts/misc/”

apt-get install twm xterm
```

But now on Ubuntu, when logging in with my VNC client, I get a black screen where usually I would see the command line. My VNC log says this

Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
MAXSOCKS=1000
02/07/06 15:47:48 Xvnc version 3.3.tight1.2.9
02/07/06 15:47:48 Copyright (C) 1999 AT&T Laboratories Cambridge.
02/07/06 15:47:48 Copyright (C) 2000-2002 Constantin Kaplinsky.
02/07/06 15:47:48 All Rights Reserved.
02/07/06 15:47:48 See [http://www.uk.research.att.com/vnc](http://www.uk.research.att.com/vnc) for information on VNC
02/07/06 15:47:48 See [http://www.tightvnc.com](http://www.tightvnc.com) for TightVNC-specific information
02/07/06 15:47:48 Desktop name 'X' (MindvateTestServer:1)
02/07/06 15:47:48 Protocol version supported 3.3
02/07/06 15:47:48 Listening for VNC connections on TCP port 5901
Xvnc: dispatch: MaxClients = 1000
xrdb: No such file or directory
xrdb: can't open file '/home/admin/.Xresources'
xsetroot:  unknown color "grey"
x-window-manager:  invalid color name "black"
x-window-manager:  invalid color name "white"
x-window-manager:  invalid color name "slategrey"
x-window-manager:  invalid color name "gray85"
x-window-manager:  invalid color name "gray85"
x-window-manager:  invalid color name "gray85"
x-window-manager:  invalid color name "slategrey"
x-window-manager:  invalid color name "gray70"

The problem seems to be with the RGB DB (first line). I've done extensive googling on the error messages, but haven't come up with a solution.

Can anyone help?

H

PS I tried to install x-window-system-core, to see if that sorts out the problem, but it just hangs on "Setting up xserver-xorg"...

---

### Post by mscman on 2006-07-02
Why do you need to use VNC?  Since a server install doesn't have X installed on it (at least not by default), couldn't you just ssh in?  It should give you the same results.

---

### Post by Randomskk on 2006-07-02
If all you're using VNC for is a command line, then SSH is **definitely** the better option.
Do this:
```

sudo apt-get install openssh-server

``` Then make sure no firewall is blocking port 22, and do this from another linux computer:
ssh username@serverIP
and answer "yes" to the key question and type in your password.

If you're on windows for the other computer, download puTTY, it's an SSH program for windows that works nicely.

---

### Post by hagen00 on 2006-07-02
Well, I wanted to use VNC to install OpenOffice.org. I use OOo to do document conversions on the server. VNC would then also be useful for debugging my marcros on the server. Of course I do all the other stuff through SSH. 

I've actually given up. What I'm going to do is do the conversions on another server that does have X installed. Very strange that stuff that worked on Debian Sarge is not working on Ubuntu...anyway. Doesn't matter now. 

Thanks anyways.

---

