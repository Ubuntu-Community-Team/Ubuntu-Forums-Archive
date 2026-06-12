---
title: "VNC on a Ubuntu server (EC flavor)"
date: 2011-04-01
forum: Server Platforms
---

### Post by wcorey on 2011-04-01
*** would someone pls move this to ubuntu thread? ****

Running, in this case, an 11.04 server under UEC. The instance starts perfectly. I can add specialized packages as advertised using cloud-init.

I want to configure a vncserver on the instance.

Here are the packages I've added:

```
packages:
- tomcat6
- tomcat6-admin
- mysql-server
- euca2ools
- iperf
- apache2
- vnc4server
- xinetd
- vim
- gnome-session-bin
- xfonts-scalable

```

Here is the xstartup file
```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
# x-window-manager &
gnome-session &

```

I start vncserver as vncserver -geometry 1440x900 (as that is the screen I use)

vncserver starts perfectly, here is the log:
```

Xvnc Free Edition 4.1.1 - built Apr  9 2010 18:47:36
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc


Fri Apr  1 18:29:05 2011
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/, removing from list!
Fri Apr  1 18:49:13 2011
 Connections: accepted: 0.0.0.0::33536
 SConnection: Client needs protocol version 3.8
 SConnection: Client requests security type VncAuth(2)

Fri Apr  1 18:49:18 2011
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565
 VNCSConnST:  Client pixel format depth 24 (32bpp) big-endian rgb888

```

Note: I have the type 1 fonts from the xfonts-scalable package.

When I connect to the 5901 port I get a gray hatched screen with the large twm cursor and an unmovable small black cmd window in the top left.

Any suggestions?

---

### Post by Azdour on 2011-04-06
Hi

The lines that xstartup tells you to uncomment I usually leave commented. Maybe try this to see if that fixes your issue.

---

### Post by arrrghhh on 2011-04-06
Why are you using VNC on a Server install?  There's no GUI, just use SSH.  Forward apps over X if you need to.

---

### Post by HermanAB on 2011-04-06
Howdy,

VNC is mostly a Windows thing.  On Linux, VNC is almost always the wrong solution.

On the server version, the SSH daemon is enabled by default.  It is secure and it works.

---

### Post by wcorey on 2011-04-06
> **arrrghhh said:**
> Why are you using VNC on a Server install?  There's no GUI, just use SSH.  Forward apps over X if you need to.

Yes, I understand there is no GUI. I've been using Linux for over a decade, I understand the difference between desktop edition and server edition. However what you guys don't realize is, as far as thin client, the better approach is to put up a Linux server with vncserver where users can VNC in and have the 'power' of a much more capable machine.

To the reply that VNC is mostly for Windows, no it isn't RDP is mostly for Windows, If you have 500, 1000 or more Linux desktops to manage then there are 500-1000+ security exposures. However if these are smaller machines with NO direct access to the internet then all you have to secure is 1 (or a couple) servers. There is a class of users, esp now with the proliferation of Windows on every Dell, that aren't so enamoured with bang hash damnits.  I am looking for a minimal graphical user interface, not a working version of Windows.

I didn't want to start a flame war or philosophical conversation or lessons on how to use a computer. So, I certainly do appreciate everyone's comments (thank you) but where I work, there are hundreds, maybe over a thousand CentOS servers, upon which several run vncserver, which is way different than 1,000 desktop systems that happen to run production. I don't need the apps, the games, the X system utilities, just a very minimal GUI running under a server.

---

### Post by egpetrich on 2011-04-06
I would agree with Azdour. Your xstartup is calling the system-default xinitrc. If I remember correctly, using "exec" means that you execute that xinitrc script and never return. Therefore anything after that in your xstartup is irrelevant.

Hmm... My Ubuntu server with VNC installed is 8.10, so take this with a grain of salt, but I don't see "/etc/vnc/xstartup". You might want to check this on your system, since that "exec" would once again (I think) render everything after it superfluous.

So try commenting out the lines:

```
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc
```

and see what happens.

---

