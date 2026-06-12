---
title: "Semi-headless Server VNC"
date: 2011-08-25
forum: Server Platforms
---

### Post by spookybathtub on 2011-08-25
Hi everyone.  I'm a mac guy, so I am pretty familiar with terminal, but I'm very new to linux.  Hopefully someone can help solve this problem:
I've been reading several threads regarding headless VNC operation, but none of them apply to my situation exactly.  I'm running Ubuntu 10.04 on a semi-headless machine.  It's primary job is a headless server, but I also want to use it occasionally as an HTPC with Boxee.  So it's connected to my 1080p TV via HDMI.  My video card is an integrated Radeon HD 4250.

When I connect using VNC, I see the 1920x1080 display correctly, and can move the mouse, but I can't see the results of what I'm clicking on.  e.g. if I click the Applications menu, I don't see the menu open.  If I turn on the TV, I can see that all my keyboard/mouse actions are being recognized just fine, so I could essentially use VNC as a wireless input device. But I need to be able to use it without the TV on.

I've tried the xorg.conf settings [here]("http://ubuntuforums.org/showthread.php?t=1297815"), but that does nothing for me.  I've attached my xorg.conf.

Any suggestions would be greatly appreciated.

---

### Post by Wayne_V on 2011-08-25
I've never configured X for VNC headless but I do a similar sort of thing with x11vnc.   I put this in /etc/rc.local:

/usr/bin/x11vnc -shared -bg -o /var/log/x11vnc.log -avahi -forever -auth /home/<user>/.Xauthority -rfbauth /home/<user>/.vnc/passwd -ncache 10 -xkb -display :0

then create create the .vnc/passwd file as <user> with vncpasswd

then, you can connect using any vnc client and have full control over your :0 display.

You don't need to add that to rc.local if you don't want -- you can just ssh in and kick off x11vnc with out the -bg I think, and then when the vnc client exits x11vnc will exit as well.   The -xkb option is a tweak for vnc clients on MAC - without it the shift key doesn't work.  You may not need it.

---

### Post by spookybathtub on 2011-08-26
Great tip.  Thanks.  I tried x11vnc and it seems to handle the headlessness just fine.  I changed your init script a little, adding ```
-users +elliott
``` because rc.local runs as root, which just seems unnecessary for this.
And I had to remove the [FONT="Courier New"]-ncache[/FONT] because my favorite VNC client (Apple Remote Desktop) couldn't handle it.  It shows 10 copies of the display 'tiled' vertically.  Anyone else experience that?
So far, redrawing the screen is very slow, especially on mouseover events.  Like 4 seconds to open a submenu in the Applications menu.  Maybe this is because I'm not using [FONT="Courier New"]-ncache[/FONT] ]?

---

### Post by Wayne_V on 2011-08-26
if you are on the same lan you shouldn't have any problems with speed.  I am sitting in Germany and I use VNC to manage my mothers computer in the US.   In one terminal window I tunnel the VNC connection (x11vnc already running there):

ssh -N -t -L 5902:localhost:5900 user@remotecomputer

and then in another I connect the tightvnc client:

java -cp ~/tightvnc/classes VncViewer HOST localhost PORT 5902 Encoding Tight "Compression level" 9 "Scaling factor" 90

and have no problems.  The speed is not bad at all, especially considering she only gets about 300k on her DSL on a good day ...

I would give the tightvnc client a try.

---

### Post by Lars Noodén on 2011-08-26
+1 for tightvnc client and server

---

