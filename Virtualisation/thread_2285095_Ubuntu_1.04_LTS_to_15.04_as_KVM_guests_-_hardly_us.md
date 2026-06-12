---
title: "Ubuntu 1.04 LTS to 15.04 as KVM guests - hardly usable - spice/qxl issues"
date: 2015-07-03
forum: Virtualisation
---

### Post by edoardo on 2015-07-03
Hi
I have abandoned using Ubunutu/Mint 14.04 to 15.04 as VM guests in KVM becuase of the issues encounterd using the spce-optimized qxl video driver
Namely this critical one
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-qxl/+bug/1261916](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-qxl/+bug/1261916)
but there are other like
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-qxl/+bug/1464729](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-qxl/+bug/1464729)

Using spice rather than VNC is really essential for workstation/graphical virtualization using KVM.
It provides performance, clipboard integration, and dynamic resolution changes with the guest window being resized. 
All things given for granted if you use VMWare or Virtualbox, but QEMU/KVM is pretty good too if using spice.

Except that on the recent Ubuntu/Mint it really is too buggy.
Fonts disappear - requiring a logout becuade the UI becomes unusable.
Dynamic resolution does not work

Fedora 22 guests works like a charm, snappy.

If anyone has found a fix / workaround - could please share here and on launchpad?
thanks

---

### Post by TheFu on 2015-07-04
Yes, VNC sucks. Use x2go for 2-3x the performance and automatic ssh tunnels. Works great for normal "productivity" applications. I use it daily for about 2 yrs - before x2go, used FreeNX.  People using VNC don't know how bad they have it.  It doesn't have dynamic resolution - just use lxrandr to set the resolution you want.

No, spice is NOT required for workstation use, but I've heard it works well on Fedora, which makes sense as Redhat is contributing - I think oVirt integrates with spice.

If you need high-end graphics, perhaps a VM isn't the best answer? At least, not yet.  There is always GPU passthru, assuming the user is sitting behind the VM host machine and have an extra GPU to completely assign to the VM. Not really an option for many people, plus the HW to make this work is really specific and picky.

---

