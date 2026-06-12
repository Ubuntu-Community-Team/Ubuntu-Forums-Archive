---
title: "Ubuntu 12.10 ARM Rootfs for Tablet"
date: 2012-10-28
forum: Ubuntu Dev Link Forum
---

### Post by Igneo676 on 2012-10-28
Building a Rootfs for my Motorola Xoom, using root stock and [this]("https://wiki.ubuntu.com/ARM/RootfsFromScratch/") guide. Stuck the rootfs to my sdcard and put together a boot.img that pointed to that partition as root.

Whenever I boot, it tells me that the /init is not found.

I've double checked that the partition is not corrupt, that it's looking at the correct partition, but no dice as far as booting goes. Did I miss something while creating my rootfs?

---

### Post by mc75 on 2012-11-15
At the bottom of Root Stock Guide there are two email adrresses that You might get some help.

I am trying to install/build/get any kind of Linux-base system on my device with XScale processor. The one You have is a dual-core CPU, as far as i know there are some issues with non-single cores CPU's (that Linuxes have booting up on PPC's). That's all I know...

In the mean time, meybe You could point me somewhere? ;]

[POST] for Symbol / Motorola MC75A6 [http://ubuntuforums.org/showthread.php?t=2084150]("http://ubuntuforums.org/showthread.php?t=2084150")

I would also recomend You to double check Your build-in BOOTing software...home page or some wiki's could point You something.
Good luck!

---

