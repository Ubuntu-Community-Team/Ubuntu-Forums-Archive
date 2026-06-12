---
title: "Ubuntu Studio 64 + nV ION = No accel?"
date: 2010-07-13
forum: Ubuntu Studio
---

### Post by theraje on 2010-07-13
Hey guys, I'm having problems with Ubuntu Studio. I installed the 64-bit version 10.04 with rt kernel on a Zotac MAG (Atom 330 + nVidia ION). I installed the 32-bit version of Ubuntu Studio at first, and had no problems other than Wi-Fi not working (which worked in vanilla Ubuntu 32, but that's another matter). When I reformatted and put Ubuntu Studio 64-bit in, everything works except the nVidia drivers.

The drivers load, but I can't enable desktop effects, and when I open the nVidia settings panel, it says that the driver isn't running and asks to run 'sudo nvidia-xconfig' (which I tried, and it cause the X server to fail upon reboot, so I had to revert). Hardware Drivers says that the driver is installed and running, but...

Is this a problem with Ubuntu Studio 64-bit Lucid, or is something else going on? Should I revert to 32-bit, and if so, should I run vanilla Ubuntu and install the Studio packages manually (so my Wi-Fi works again)? (I want to get it sorted if I can without reinstalling if possible.)

Any and all help is appreciated!!

---

### Post by cchhrriiss121212 on 2010-07-14
Try removing and reinstalling the driver. For wireless see this thread:
[http://swiss.ubuntuforums.org/showthread.php?t=1525705](http://swiss.ubuntuforums.org/showthread.php?t=1525705)

---

### Post by theraje on 2010-07-14
Thanks, I already tried to remove the driver and load it back... but it still didn't go.

Anyway, I figured I'd just reload Ubuntu 10.04 32-bit, and installed the Ubuntu Studio meta packages I needed. It works (though I don't yet know how much not having the realtime kernel will affect me).

---

