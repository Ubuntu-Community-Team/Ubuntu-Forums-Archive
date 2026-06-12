---
title: "[CROSS] Ubuntu 9.10 vnc server"
date: 2009-12-22
forum: Server Platforms
---

### Post by nuzzosono on 2009-12-22
Posted also in ubuntu.it forum.
 
Hi everybody, I'm new to Ubuntu, I've set up a server to use as a Hylafax server, everything is working now, but I have a problem with the remote control of the server.
I have installed SSH, and I can access the machine from everywhere (the lan and outside with VPN).
Now I'dd like to make remote desktop session working, I tried vino, vnc4server, x11vnc and tightvncserver but I have always the same problem, the remote screen appear empty, I can move the mouse and click everywhere, but I can't see menu bars, icons, text, etc.
I enclose two screenshot to clarify the issue.
 
[[COLOR=#5e3a04]http://img692.imageshack.us/img692/2972/desktopwindow.jpg[/COLOR]]("http://img692.imageshack.us/img692/2972/desktopwindow.jpg")
 
[[COLOR=#5e3a04]http://img51.imageshack.us/img51/4784/loginwindow.jpg[/COLOR]]("http://img51.imageshack.us/img51/4784/loginwindow.jpg") 
 
Thank you in advance from any help.

---

### Post by krunge on 2009-12-22
> **nuzzosono said:**
> I tried vino, vnc4server, x11vnc and tightvncserver but I have always the same problem, the remote screen appear empty, I can move the mouse and click everywhere, but I can't see menu bars, icons, text, etc.
I'm not sure if this is your problem, but with x11vnc try the "-noxdamage" option (search forums for "noxdamage" for more info.)  Or, if compiz is active then disable it.

Also, be sure you are connecting to the vnc server you think you are.  Watch their terminal or logfile output when the vncviewer connects to make sure.  Sometimes people think they are trying many different vnc servers but every time they are connecting to the same one (e.g. vino.)

(BTW it surprises me that the RAM-only virtual servers vnc4server and tightvncserver would have the same problem as the hardware based ones...)

---

### Post by doas777 on 2009-12-22
> **krunge said:**
> I'm not sure if this is your problem, but with x11vnc try the "-noxdamage" option (search forums for "noxdamage" for more info.)  Or, if compiz is active then disable it.

Also, be sure you are connecting to the vnc server you think you are.  Watch their terminal or logfile output when the vncviewer connects to make sure.  Sometimes people think they are trying many different vnc servers but every time they are connecting to the same one (e.g. vino.)

(BTW it surprises me that the RAM-only virtual servers vnc4server and tightvncserver would have the same problem as the hardware based ones...)

this is likely the problem. the way to test it, is to connect, and disconnect, then reconnect quickly. you may see your desktop now, but you won't be able to manipulate it, if krunge's hunch is correct.

the problem is compiz (desktop effects). you can disable them on the server, if you never need them. 

alternatively, you can login over ssh and run "metacity --replace", or just login to vino, and blindly run the command with Alt+F2. after turning metacity back on, you  may have to close and reopen your connection. 

good luck

---

### Post by nuzzosono on 2009-12-23
> **doas777 said:**
> this is likely the problem. the way to test it, is to connect, and disconnect, then reconnect quickly. you may see your desktop now, but you won't be able to manipulate it, if krunge's hunch is correct.
 
the problem is compiz (desktop effects). you can disable them on the server, if you never need them. 
 
alternatively, you can login over ssh and run "metacity --replace", or just login to vino, and blindly run the command with Alt+F2. after turning metacity back on, you may have to close and reopen your connection. 
 
good luck
 
Unfortunatelly none of your suggestions did the trick, I'm connecting to the right vnc server, compiz is disabled (I don't need it), the problem is still there.
More I can tell is that the monitor connected to the server is working perfectly and when I remotely controll the machine I can see the mouse moving as windows and icons, everythink is ok.
Only the screen that is sent to the remote machine is like freezed to the screenshot that I enclosed in my previous message.
 
p.s. metacity --replace give me: error in window manager: unable to open X display, even if I'm logged in or not.

---

### Post by doas777 on 2009-12-23
hmmmm. not sure what other advice to give you, except to look into freenx instead of VNC (it's superior in all ways except that it does not share a desktop session.)

---

### Post by krunge on 2009-12-23
> Unfortunatelly none of your suggestions did the trick, I'm connecting to the right vnc server, compiz is disabled (I don't need it), the problem is still there.
You even get this with "vncserver :5" (e.g. vnc4server) and then connecting to VNC display :5 with a vncviewer?

Please post the log of vncserver including the viewer connection attempt.  It should go into something like ~/.vnc/hostname:5.log  There is something very strange  going on if you get those blank regions with vncserver...

---

### Post by nuzzosono on 2009-12-23
> **krunge said:**
> You even get this with "vncserver :5" (e.g. vnc4server) and then connecting to VNC display :5 with a vncviewer?

Please post the log of vncserver including the viewer connection attempt.  It should go into something like ~/.vnc/hostname:5.log  There is something very strange  going on if you get those blank regions with vncserver...

maybe you point me in the right direction, here is the log:

```
Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Wed Dec 23 19:46:53 2009
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5905
 vncext:      created VNC server for screen 0
[B]error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
exec: 5: /etc/X11/xinit/xinitrc: Permission denied[/B]

Wed Dec 23 19:47:11 2009
 Connections: accepted: 192.168.0.203::49173
 SConnection: Client needs protocol version 3.3

Wed Dec 23 19:47:16 2009
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565
 VNCSConnST:  Client pixel format depth 8 (8bpp) bgr233

Wed Dec 23 19:47:43 2009
 Connections: closed: 192.168.0.203::49173 (write: Broken pipe (32))
 SMsgWriter:  framebuffer updates 2
 SMsgWriter:    hextile rects 4, bytes 596533
 SMsgWriter:    raw bytes equivalent 1571901, compression ratio 2.635061
```

I think that the highlited errors are meaning that something is wrong in my ununtu install.

Can you give me an hand?
Thanks!

---

### Post by nuzzosono on 2009-12-23
> **nuzzosono said:**
> maybe you point me in the right direction, here is the log:

Can you give me an hand?
Thanks!

p.s. in /usr/share/fonts/X11 I have this folders:

100dpi  75dpi  encodings  misc  Type1  util

---

### Post by doas777 on 2009-12-23
I seem to recall the need to change some parameters for the login screen when installing a full vnc server. check out this [http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

---

### Post by krunge on 2009-12-23
I installed vnc4server on ubuntu 9.10 and ran "vncserver :1"

In the hostname:1.log log file I see the same SecurityPolicy warning and TTF/OTF/CID fonts warning that you get.  So I don't think they are problems.

The /etc/X11/xinit/xinitrc warning you have is probably a major problem.  I don't get that warning. Here is my file:
```

fred@test1:~$ ls -l /etc/X11/xinit/xinitrc
-rw-r--r-- 1 root root 226 2009-04-29 16:53 /etc/X11/xinit/xinitrc
fred@test1:~$ dpkg -S /etc/X11/xinit/xinitrc
xinit: /etc/X11/xinit/xinitrc

```
What does yours look like? Does it exist? Is it readable by you?

For my test the vncserver desktop looked and acted perfectly fine.

BTW my "vncserver :1" works for both the default minimal "twm" window manager and also for the GNOME window manager, which I get by editing ~/.vnc/xstartup like so (commenting out the twm line with '#' and adding gnome-session line):
```

...
#twm &
dbus-launch --exit-with-session gnome-session &

```

---

### Post by nuzzosono on 2009-12-23
> **doas777 said:**
> I seem to recall the need to change some parameters for the login screen when installing a full vnc server. check out this [http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

can I do this:

1. Enable XDMCP
System->Administration->Login Screen Setup
Tab Security->Enable XDMCP
Tab XDMCP--> You can disable "Honor Indirect Requests"

from ssh terminal or do I have to reach the server fisically?

Anyway I think that my system miss some fonts during installation that's why it cannot show any text via vnc session.

---

### Post by nuzzosono on 2009-12-23
> **krunge said:**
> I installed vnc4server on ubuntu 9.10 and ran "vncserver :1"

In the hostname:1.log log file I see the same SecurityPolicy warning and TTF/OTF/CID fonts warning that you get.  So I don't think they are problems.

The /etc/X11/xinit/xinitrc warning you have is probably a major problem.  I don't get that warning. Here is my file:
```

fred@test1:~$ ls -l /etc/X11/xinit/xinitrc
-rw-r--r-- 1 root root 226 2009-04-29 16:53 /etc/X11/xinit/xinitrc
fred@test1:~$ dpkg -S /etc/X11/xinit/xinitrc
xinit: /etc/X11/xinit/xinitrc

```
What does yours look like? Does it exist? Is it readable by you?

For my test the vncserver desktop looked and acted perfectly fine.

BTW my "vncserver :1" works for both the default minimal "twm" window manager and also for the GNOME window manager, which I get by editing ~/.vnc/xstartup like so (commenting out the twm line with '#' and adding gnome-session line):
```

...
#twm &
dbus-launch --exit-with-session gnome-session &

```


this is mine:

> root@faxserver:/etc/X11/xinit# more xinitrc
#!/bin/bash
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession

and my xstartup:


> #!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
startlxde &

---

### Post by krunge on 2009-12-23
> **nuzzosono said:**
> this is mine
Please show "ls -l" for it.  Are you running vncserver as an ordinary user?  Can that user read this xinitrc file?  Your log message "permission denied" suggests it can't be read.

---

### Post by doas777 on 2009-12-23
> **nuzzosono said:**
> can I do this:

1. Enable XDMCP
System->Administration->Login Screen Setup
Tab Security->Enable XDMCP
Tab XDMCP--> You can disable "Honor Indirect Requests"

from ssh terminal or do I have to reach the server fisically?

Anyway I think that my system miss some fonts during installation that's why it cannot show any text via vnc session.

not so far as I am aware

---

### Post by nuzzosono on 2009-12-23
> **krunge said:**
> Please show "ls -l" for it.  Are you running vncserver as an ordinary user?  Can that user read this xinitrc file?  Your log message "permission denied" suggests it can't be read.

those are the permission on that file:

-rw-r--r-- 1 root root  226 2008-05-29 14:53 xinitrc

I always login as a root.

---

### Post by nuzzosono on 2009-12-24
> **nuzzosono said:**
> can I do this:
 
1. Enable XDMCP
System->Administration->Login Screen Setup
Tab Security->Enable XDMCP
Tab XDMCP--> You can disable "Honor Indirect Requests"
 
from ssh terminal or do I have to reach the server fisically?
 
Anyway I think that my system miss some fonts during installation that's why it cannot show any text via vnc session.
 
Ok this solution if working for me, unfortunatelly I'll not be able to control an existing session, but I can login to a new one.
 
I have the same problem reported in [this thread]("http://ubuntuforums.org/showthread.php?t=1355786"), so hi have to stop gdm and start gdm everytime I want to login, if somebody in the meantime found a solution.... 
 
Thank you and have a merry christmas!!!!

---

