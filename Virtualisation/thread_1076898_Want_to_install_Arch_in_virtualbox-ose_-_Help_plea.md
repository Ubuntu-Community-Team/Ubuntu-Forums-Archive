---
title: "Want to install Arch in virtualbox-ose - Help please!"
date: 2009-02-21
forum: Virtualisation
---

### Post by calrogman on 2009-02-21
As a fairly new Linux user who wants to learn about what makes Linux tick, I have decided I am going to install Arch Linux in Virtualbox-ose.

As far as I am aware I need to install virtualbox-ose-modules-$KERNEL, unfortunately, Arch 2009.2 uses 2.4.26 and the most recent virtualbox-ose-modules package available in the repos is 2.4.24-23  What should I do?

EDIT: OK, I realize I was totally wrong and that the kernel is that of the host machine and not the guest, I have also added myself to the necessary group, but when I try to run the setup I get the following printed to the screen, these are the 3 last lines printed.

> 
[<c0433865>] start_kernel+0x2e1/0x35d
[<c043335b>] unknown_bootoption+0x0/0x1db
---[ end trace 4eaa2a86a8e2da22 ]---


If anyone knows what is wrong please help, if you need to know I am trying to run the Arch install from archlinux-2009.2-core-i686.iso and my laptop definitely runs on a i686 as the output of 
```
uname -a
```
shows.

> Linux Linx 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux


EDIT: Here, have a screenshot!
EDIT: Tested with 2 convenient Linux isos I keep on my Desktop.  Xubuntu 8.10 and Mint 6 work.
EDIT: Awesome!  A 300 MB game of Space Invaders, apparently SI works then!

EDIT: I have updated VB and now it is running perfectly!:D

---

