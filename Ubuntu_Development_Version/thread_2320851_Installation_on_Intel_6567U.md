---
title: "Installation on Intel 6567U"
date: 2016-04-18
forum: Ubuntu Development Version
---

### Post by tokka on 2016-04-18
Hi

I'm trying to install Ubuntu 16.4 Beta 2 on a laptop with the new Intel 6567U CPU, that has the Iris 550 GPU.

Installation goes well, Intel wireless HW is found and works, however after the install I can't get beyond the login screen.

When I log in, Mir (?) seems to get started, the mouse pointer appears and can be moved, but Unity doesn't appear.

When I drop to a terminal, the contents of the X11 log look OK.

Any ideas?

There are probably going to be a rush of new laptops with this hardware, so Ubuntu LTS needs to support it.

---

### Post by grahammechanical on 2016-04-18
> When I log in, Mir (?) seems to get started,

Not Mir. Not default in any Ubuntu desktop version. Maybe 16.10. But no one is promising. It is the Gnome 3 desktop environment & the Unity user interface that is not loading.

How new is "new?" Too new for there to be a driver for that video adapter? There is something that you could try.

At the boot menu select Advanced options for Ubuntu and then select a recovery mode kernel. And at the recovery menu select Resume. That may get you to a working desktop with a fall back open source video driver. Take it from there.

Regards.

EDIT: The CPU is a Skylake model. But 16.04 does have Linux kernel 4.4 and that does have some Skylake support. On that point, support has to come not from Ubuntu developers but from the Linux kernel developers & Intel and it has to come out far enough in advance to get into a Ubuntu release.

---

### Post by tokka on 2016-04-18
> **grahammechanical said:**
> Not Mir. Not default in any Ubuntu desktop version. Maybe 16.10. But no one is promising. It is the Gnome 3 desktop environment & the Unity user interface that is not loading.


Ah. I haven't been following things, and so assumed that was the case especially when I found gnome-fallback had gone. 


> **grahammechanical said:**
> How new is "new?" Too new for there to be a driver for that video adapter?

New:) Intel have an installer with a driver for 15.10+.

14.04 installer works fine and boots, however I can't install the the correct video driver as the kernel is too old.

And annoyingly the Intel installer is graphical, so I can't run it on 16.04

I can't start vino as I can't log in, I tried x11vnc but it just gives me a black screen.

---

