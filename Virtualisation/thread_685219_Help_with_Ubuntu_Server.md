---
title: "Help with Ubuntu Server"
date: 2008-02-02
forum: Virtualisation
---

### Post by Thirtysixway on 2008-02-02
I am currently running Ubuntu 7.10 Server Edition.  I tried to install VMware, but it says that I'm missing libXtst.so.6 when I try to enter the serial code for it during installation.

It is to my knowalege that this is part of xserver?  How can I install VMWare without installing a windows manager...

I have another VMware product installed on my other computer that lets me connect remotely.  I've done this before on a normal Ubuntu desktop install, but not server.

Any ideas of what to do?  I really don't want to install xserver because that's the whole reason i switched to server edition, to get away from the GUI. :confused:

---

### Post by mbrush on 2008-02-02
Isn't VMWare a totally GUI program?  
I've only used the player, but I don't see how it could run without X.  I've never seen VMware run in a CLI installation.

You could just install the meta-package 'xorg' and that will put X without a windows manager or anything else.

I don't think you'll be able to move/resize VMWare in X by itself, so maybe make it run FullScreen on startup.

I did something similar with firefox, where it ran on startup in fullscreen under just X, and it was pretty cool until I opened any dialog box and remember there's no window manager.

Good Luck

---

