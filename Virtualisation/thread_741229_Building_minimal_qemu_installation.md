---
title: "Building minimal qemu installation"
date: 2008-03-31
forum: Virtualisation
---

### Post by swarog on 2008-03-31
Hi!

I am trying to build a minimal qemu installation of Linux system to play with kernel. The qestion is how do I prepare a virtual disk for the system?

I have created virtual hda image in raw format as described here [http://www.osdev.org/osfaq2/index.php/Disk%20Images%20Under%20Linux](http://www.osdev.org/osfaq2/index.php/Disk%20Images%20Under%20Linux) . I created one primary partition on it (200M, ext3). Now if I mount it using loopback device, I can see that partition with fdisk. Then I have copied /bin, /sbin, /etc and /dev to that partition. It looks like ok when used through /dev/loop0. But when I launch the kernel with that raw disk, it says it can not find init, Although /sbin/init is certainly there on the raw disk file. I tried supplying the krenel with init=/bin/sh option but that did not help. 

What am I doing wrong?

---

