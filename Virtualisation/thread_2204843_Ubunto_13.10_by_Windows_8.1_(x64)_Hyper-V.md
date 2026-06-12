---
title: "Ubunto 13.10 by Windows 8.1 (x64) Hyper-V"
date: 2014-02-10
forum: Virtualisation
---

### Post by magne2 on 2014-02-10
Installed Ubuntu 13.10
Using Hyper-V viewer, screen resolution is 1152x864 only.
Ux is extremely slow, e.g. showing a terminal (alt-ctrl-t) takes at least 10 seconds.

Shouldn't be that slow I guess ?
How to increase the resolution ?

---

### Post by IPvFletch on 2014-02-10
Not sure about resolution, it is probably the emulated video card and lack of driver support on Ubuntu which causes the lower resolution.

You should check if you have Hardware Accelleration enabled/available in your BIOS.. something like this:

[http://h30434.www3.hp.com/t5/Desktop-Hardware/Enable-hardware-virtualization-in-BIOS/td-p/1152355](http://h30434.www3.hp.com/t5/Desktop-Hardware/Enable-hardware-virtualization-in-BIOS/td-p/1152355)

---

### Post by magne2 on 2014-02-10
Thanks and yes, virtualization is enabled in BIOS.
I just tried to give it 4 virtual cpu's and 2GB of memory and it helps quite a bit, anyway it is much slower than a Windows Server 2012 R2 Datacenter edition running in the same hyper-v with win 8.1 as host (with less memory and only 1 virtual cpu).
This is far from good enough and makes me feel it is close to useless.
Should any kind of integration services be installed ? (how ?)
Would it be better with VNC or xrdp or similar ? (I tried both, but cannot get them working for some reason, the xrdp gives be just a desktop background without any icons on it.

---

### Post by brokenhachi on 2014-02-12
In VMWare, the virtual console is bad resolution and extremely slow until you install the vmtools.. I've never used Hyper-V but they have something similar? have you installed it to the guest? [http://www.eweek.com/networking/microsoft-releases-linux-integration-services-3.5-for-hyper-v.html](http://www.eweek.com/networking/microsoft-releases-linux-integration-services-3.5-for-hyper-v.html)

---

### Post by magne2 on 2014-02-14
I suppose your are touching the problem.
Some web pages states that Microsoft (Hyper-V) does not support Ubuntu (and most other "desktop" Linux distros), other states that all is built in to the .iso file.
I have no clue, anyone may hint ? (perhaps some Integration Services to be exposed to Ubuntu and installed ??)

---

### Post by sblake on 2014-04-14
I wonder if anyone had an update on this?

As for the screen resolution, this link has the answer:

[http://askubuntu.com/questions/384602/ubuntu-hyper-v-guest-display-resolution](http://askubuntu.com/questions/384602/ubuntu-hyper-v-guest-display-resolution)

You need to change /etc/default/grub and add a few lines in there. It forces the display to a certain resolution, which is a good fix.

But I'm still having performance issues... I'm running a Surface Pro 2 (i5 quad core Haswell) so I'm pretty sure it's powerful enough. But the mouse still lags and windows take a while to open ... and when they do, it does it slooooowly (which looks terrible in Unity, btw :P Slowly fading in at 2 frames per second).

Anyone else experiencing this? Anyone not? If not, post your setup!

---

### Post by sblake on 2014-04-14
It's all built it, btw. You don't need to add it to Ubuntu.

---

