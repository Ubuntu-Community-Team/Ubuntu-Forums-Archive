---
title: "Workstation 6.5.3-185404 problem with Jaunty (9.04)"
date: 2009-09-21
forum: Virtualisation
---

### Post by Kissaki on 2009-09-21
Hi All,

I have been experiencing some problem with Workstation 6.5.3 on my newly installed Jaunty (32-bit, 2.6.28-15-generic).

I downloaded the latest bundle file and installed it according to documentation ([https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation)). The installation was successful and it created shortcuts under System Tools> VMware Workstation.

When I click the link, the kernel module updater appears and asks me to allow it to compile modules in running kernels. After clicking "install", it gives the error that it cannot build the kernel (see ss1.png). The content of the log is:

dem@Kuzey:/tmp$ sudo more /tmp/vmware-root/setup-22702.log
Sep 21 14:46:43.812: app| Log for VMware Workstation pid=22702 version=6.5.3 build=build-185404 option=Release
Sep 21 14:46:43.812: app| Host codepage=UTF-8 encoding=UTF-8
Sep 21 14:46:43.812: app| Logging to /tmp/vmware-root/setup-22702.log
Sep 21 14:46:44.802: app| Extracting the sources of the vmmon module.
Sep 21 14:46:44.814: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT
_SMP=1 HEADER_DIR=/lib/modules/2.6.28-15-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.3.3
dem@Kuzey:/tmp$ 

Although I already tried the suggestion at ([http://ubuntuforums.org/showthread.php?t=1040351](http://ubuntuforums.org/showthread.php?t=1040351)), it still didnt worked, and I am still unable to make the latest VMware to work on my Jaunty.

Can someone knowledgeable give a hand to this newbie of Jaunty?

Thanks in advance...

---

