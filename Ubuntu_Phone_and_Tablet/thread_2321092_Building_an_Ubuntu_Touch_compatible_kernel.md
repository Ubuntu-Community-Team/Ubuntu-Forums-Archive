---
title: "Building an Ubuntu Touch compatible kernel"
date: 2016-04-20
forum: Ubuntu Phone and Tablet
---

### Post by Incognegro on 2016-04-20
I am currently trying to build an Ubuntu Touch-compatible kernel for use with the Xperia Z5 Compact. I have been following the [How to build and flash a Linux kernel for AOSP supported devices guide]("http://developer.sonymobile.com/knowledge-base/open-source/open-devices/how-to-build-and-flash-a-linux-kernel/how-to-build-and-flash-a-linux-kernel-for-aosp-supported-devices/") and am at the point at which I have created an Ubuntu-compatible .config file but am having issues finally building the kernel (Step 7) using the .config file as I receive the following error:

make ARCH=arm64 CROSS_COMPILE=$CROSS_COMPILE -j 14
Makefile:791: *** multiple target patterns.  Stop.

I know that this error is related to vmlinux.sh which is referenced as follows on line 791 of the Makefile:

vmlinux: scripts/link-vmlinux.sh $(vmlinux-deps) FORCE

Any suggestions for debugging this problem would be greatly appreciated as googling has provided me no leads.

---

### Post by dino99 on 2016-04-20
you should find more usefull help directly asking devs on askubuntu

and this forum [http://ubuntuforums.org/forumdisplay.php?f=460](http://ubuntuforums.org/forumdisplay.php?f=460) for phone/tablet

---

### Post by Bucky Ball on 2016-04-20
*Thread moved to **Ubuntu Phone and Tablet**.*

---

### Post by Incognegro on 2016-04-22
I haven't been able to successfully compile the kernel yet given a new problem with my local SDK verison but the immediate problem seems to be solved by using ARCH=arm instead of ARCH=arm64 when building the kernel ([reference]("https://forums.oneplus.net/threads/kernel-compiling-noob-thread.381142/#post-13582337")).

---

