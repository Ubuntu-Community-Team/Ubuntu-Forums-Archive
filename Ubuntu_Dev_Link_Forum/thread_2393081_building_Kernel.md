---
title: "building Kernel"
date: 2018-05-29
forum: Ubuntu Dev Link Forum
---

### Post by jlaughto on 2018-05-29
Hi, I am new to kernel development
My target is using Mate with a RPi 3B
I want (need) to build a 4.15 or greater kernel, so I can patch it. I believe the latest is 4.17RC
I have cloned the repo v4.15-rc1 (git://git.launchpad.net/~ubuntu-kernel-test/ubuntu/+source/linux/+git/mainline-crack)
I am cross compiling with a 16.04 x86_64. I have a cross compiler installed 
I THINK I need to run the commands:
[FONT=arial]make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- bcmrpi_defconfig
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- zImage modules dtbs -j2[/FONT]

Looking for advise on building the kernel - google seems inconsistant on instructions

---

