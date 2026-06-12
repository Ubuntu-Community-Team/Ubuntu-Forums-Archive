---
title: "Why was install in free space been removed!"
date: 2010-12-07
forum: The Cafe
---

### Post by screaminj3sus on 2010-12-07
Really had no idea where to put this, but I was installing ubuntu 10.10 the otherday and noticed the "install in free space" option was pointlessly removed. I know I can use manually partition but that makes unnecessary steps in the installation process. 

One of the safest ways to install linux to dual boot with vista/7 is to use the vista/7 partition manager to shrink your partition to create free space (because if you do it from linux windows makes you chkdsk on next boot), then when you install ubuntu you could simply click "install in free space" and it always worked flawlessly. It was one of my favorite things about the ubuntu installer, and distros that don't have the option annoyed me.

Why remove the option? seems pointless to me There's more than enough space for it on the screen where it gives those options...

---

### Post by cariboo on 2010-12-07
It was replaced by the install along side of option, eliminating the extra step of resizing your windows partition first, then doing the the installation.

---

### Post by screaminj3sus on 2010-12-07
> **cariboo907 said:**
> It was replaced by the install along side of option, eliminating the extra step of resizing your windows partition first, then doing the the installation.

I did try that option but it doesnt work the same way, I have a separate partition made by windows, which is free space. When I use install alongside it ONLY sees the windows partition with no option to simply select the empty one to install in.

---

### Post by wilee-nilee on 2010-12-07
> **screaminj3sus said:**
> I did try that option but it doesnt work the same way, I have a **separate partition made by windows, which is free space.** When I use install alongside it ONLY sees the windows partition with no option to simply select the empty one to install in.

The syntax is confusing the only thing the windows disk manager can do for Ubuntu is remove partitions=unallocated space, or make a NTFS that is shared, or a fat shared as well probably.

---

### Post by screaminj3sus on 2010-12-07
> **wilee-nilee said:**
> The syntax is confusing the only thing the windows disk manager can do for Ubuntu is remove partitions=unallocated space, or make a NTFS that is shared, or a fat shared as well probably.

Yeah I generally use the windows partition manager to shrink the partition and make a new one. If you shrink it with the linux installer you have to go through a chkdsk next boot, its annoying.

Since vista the windows partition manager has the ability to resize partitions, not just create and delete them.

---

### Post by wilee-nilee on 2010-12-07
> **screaminj3sus said:**
> Yeah I generally use the windows partition manager to shrink the partition and make a new one. If you shrink it with the linux installer you have to go through a chkdsk next boot, its annoying.

Since vista the windows partition manager has the ability to resize partitions, not just create and delete them.

I just build partitions ahead of time so during the holiday break I will practice a little wubi, and regular installs to see the changes and well you know all the fun.;)

---

### Post by ugm6hr on 2010-12-09
> **cariboo907 said:**
> It was replaced by the install along side of option, eliminating the extra step of resizing your windows partition first, then doing the the installation.

This option was also always available.
I agree that the install in free space was useful. Of course, it doesn't matter to me any more, since I know what I am doing. But when still learning, I found it the easiest way to do a fresh install over an existing Ubuntu installation (when dual-booting):
delete partitions -> install in free space

---

### Post by lisati on 2010-12-09
> **ugm6hr said:**
> This option was also always available.
I agree that the install in free space was useful. Of course, it doesn't matter to me any more, since I know what I am doing. But when still learning, I found it the easiest way to do a fresh install over an existing Ubuntu installation (when dual-booting):
delete partitions -> install in free space

Same here: I've been in the habit of freeing up some space and telling the installer to use it, but probably can adjust to the current scheme when the time comes.

---

