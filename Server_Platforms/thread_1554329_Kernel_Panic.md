---
title: "Kernel Panic"
date: 2010-08-16
forum: Server Platforms
---

### Post by Tobas on 2010-08-16
Hi there,

I got a BIG problem.
Yesterday i reboot my Ubuntu-server and i get a Kernel Panic

[0.973019] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

thats it, nothing works from there

And my biggest problem is that i run on LVM

this is my setup

250 Gb HD  <-- base filesystem

LVM -- 1 TB
     - 1,5 TB
     - 1,5 TB

so my base filesystem is NOT on LVM
Is there a way to re-install my base system and recover the LVM disks, or can someone help my to find the solution for this kernel panic ?

EDIT :
Stupid me, i edit grub.cfg and now i can use my system again
But i still want to know if i can reinstall the system without losing my LVM disks


Tobas

---

