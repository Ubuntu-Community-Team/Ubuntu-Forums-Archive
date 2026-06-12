---
title: "fglrx-updates held back"
date: 2012-09-24
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by rajeev1204 on 2012-09-24
Hi

I just upgraded through the update manager but i cannot reach the desktop. Apt says the package fglrx-updates has been held back. 

How do i fall back to the free Radeon driver? 

I found that fglrx cannot be installed since it depends on a package 'xorg-video-abi-11' but it has no installation candidate.

Iam on 64 bit.

thanks

---

### Post by jfernyhough on 2012-09-24
It's dead easy (or should be).

$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

and reboot.

This should prevent X from using the configuration created by aticonfig and instead use the OSS driver for the detected graphics card.

---

