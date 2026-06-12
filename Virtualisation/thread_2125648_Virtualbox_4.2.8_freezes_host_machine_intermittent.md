---
title: "Virtualbox 4.2.8 freezes host machine intermittently"
date: 2013-03-14
forum: Virtualisation
---

### Post by reeseslover531 on 2013-03-14
Hello,

I'm running 12.10 64 bit as my host and 13.04 32 bit as my guest. I'm trying to test raring and everything boots fine but it constantly pegs my machine and freezes it up completely for a minute or two, then back to normal, then back to pegging the machine. I have 4 GB of ram and only 1GB dedicated to the guest so I don't think it's a ram issue. Any ideas?

Thanks.

Also has anyone tried running raring on KVM/QEMU the GUI is sooooooo slow. I assume it's related to no 3d acceleration

---

### Post by markbl on 2013-03-14
Virtualbox 3D is currently buggy with Ubuntu 12.10 and later guests which frequently abort (happens for me on Ubuntu 12.04, 12.10, and Mac OSX hosts). All you can do is disable 3D acceleration. Since both Unity and Gnome Shell fall back to 3D emulation using LLVMpipe that means running either in VB will be slow, depending on your host. So run a gnome classic (2D) session. Sad state of affairs but it seems to me that linux/ubuntu gets little support attention from Oracle VB nowadays.

---

