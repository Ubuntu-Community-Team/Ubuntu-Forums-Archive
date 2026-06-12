---
title: "System 76 Drivers -- vetted on Pangolin with 8.10?"
date: 2009-01-17
forum: System76 Support
---

### Post by gila_monster on 2009-01-17
Thomas et alia,

I've notice lately some odd effects with the graphics on my pangolin (panp4n). I am currently running System 76 driver 2.3.0 on Ubuntu 8.10. I never noticed the problems before the driver was updated from 2.4.x.

Generally, it shows as "artifacts" when graphics are scrolled (like when you are scrolling up and down in OpenOffice -- there is leftover text on the screen so that you see it in both the new and old position).

I'm only latched on to the System 76 driver because I started seeing this when the driver updates hit. It could well be something else, but I have to start somewhere.

Checked the NVidia drivers, seemed fine (and the same as they were before the problem showed up).

---

### Post by thomasaaron on 2009-01-17
Yeah, it's probably not the drivers.

1. Try going to System > Administration > Hardware Drivers and deactivating and then reactivating the nvidia drivers. Then reboot.

If that doesn't fix it...

2. What is the output of...
```
uname -r
```
If you're running the *-11 kernel, that *might* have something to do with it. Try booting into your grub menu (Press Esc when you see the grub countdown...) and booting into the *-9 kernel and see if the problem is there. The *-11 kernel is still proposed and not necessarily completely developed yet.

If that doesn't fix it...

3. try booting into a live CD to see if it happens there as well.

---

