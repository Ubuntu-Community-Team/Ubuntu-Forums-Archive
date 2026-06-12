---
title: "Installing VNC server on Karmic Koala Server"
date: 2009-11-06
forum: Server Platforms
---

### Post by Diubidone on 2009-11-06
Hi,

I have a Karmic Koala server with minimal gnome gui installed.

I need to install a VNC server but all the guides are for previous versions and I'm having a hard time adapting (for ex gdm.conf doesn't exist anymore). Can anybody help me with this issue?

Cheers,

---

### Post by GCoffee on 2009-11-06
Wouldnt:

sudo apt-get install tightvncserver

install a VNC server for you? OR am I missing something here over X Displays and such..

---

### Post by Diubidone on 2009-11-07
I need to install a normal vnc server on this ubuntu server I have at the office. I installed vnc4server which seems more adapt to a production server, but how do I configure it in Ubuntu 9.10?

---

### Post by Inflatable Soulmate on 2009-11-07
I'm in the exact same boat, except that I'm still using 9.04.

My guess would be that one would need to install Xorg, vnc4server, gnome, and all the little nifty gnome tools/themes you wanted to use.  What I would like to do is set up a 'proof of concept' linux dedicated gameserver for running Team Fortress 2, Left 4 Dead, and Left 4 Dead 2 dedicated servers so that I can convince my gaming clan that running linux is really the way to go.

Currently, we have a dedicated box hosted on some tremendous amount of InterNAP bandwidth in Chicago that is running Windows Server 2003.  Unfortunately, we sometimes come under DoS attacks that cripple our game servers using known UDP vulnerabilities in the source game server engine.  Windows has no real way of mitigating these attacks, but with some complicated-looking ipchains/iptables rules we could filter out the UDP packets that cause the game servers to grind to a halt.

The problem is that we have several people who help manage our dedicated server who have no linux experience, and therefore would be completely lost on the command-line.  If I could get a linux server up with gnome and a vnc server that allow us to log in under a variety of accounts with different permissions (a superuser account for OS-level maintainance, a game server admin account with the ability to modify and execute files related to the game servers, and a game server user account that is a member of a group that would allow the person to start, stop, and update the game servers without giving them access to the ability of writing to the game servers' files), then I could set up links or 'shortcuts' on the desktop of those accounts that windows users would be able to use to do what they need to do to keep the game servers running smoothly.

I would need to know what packages need to be installed to get a base Xorg/Gnome setup working over vnc4server, with the ability to log in as a variety of different user accounts.  Also, the server is headless, so I can't have it sitting there not running just because there isn't a monitor attached.  The testing will take place on a local server I have here at home, and if it is determined to meet our needs over windows, then we would basically use it as a template for setting up our dedicated box in Chicago.

Any help would be greatly appreciated.

---

### Post by wlraider70 on 2009-11-07
Are you getting errors? 
Can you tell us what error messages you get?


In all my vnc experience it has auto configured.

---

### Post by Diubidone on 2009-11-10
Here's the log form .vnc/ directory:

Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Tue Nov 10 17:28:47 2009
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
exec: 5: /etc/X11/xinit/xinitrc: Permission denied

Tue Nov 10 17:29:02 2009
 Connections: accepted: 10.144.13.37::44297
 SConnection: Client needs protocol version 3.8
 SConnection: Client requests security type VncAuth(2)

Tue Nov 10 17:29:09 2009
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565
 VNCSConnST:  Client pixel format depth 24 (32bpp) little-endian rgb888

Tue Nov 10 17:29:21 2009
 Connections: closed: 10.144.13.37::44297 (Clean disconnection)
 SMsgWriter:  framebuffer updates 13
 SMsgWriter:    hextile rects 15, bytes 2518858
 SMsgWriter:    raw bytes equivalent 6677216, compression ratio 2.650890

At remote connection I get the display attached.Thanks!

---

### Post by Diubidone on 2009-11-13
Anyone can give me a hint?

---

### Post by Diubidone on 2009-11-17
Ok I partially solved this issue following this instructions:

[http://www.ehow.com/how_5089245_install-vnc-server-ubuntu.html](http://www.ehow.com/how_5089245_install-vnc-server-ubuntu.html)

The only problem now is that if I log out from the vnc instance the VNC server goes down and I need to restart in another display with vnc4server command.

Anyone can help me with that?

---

