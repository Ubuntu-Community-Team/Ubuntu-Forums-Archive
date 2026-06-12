---
title: "AC Adapter on Panp4n"
date: 2009-11-16
forum: System76 Support
---

### Post by 3Miro on 2009-11-16
I am currently using Kubuntu 9.10 on Panp4n, however, I am posting on all variants since this bug seems to be kernel related and Kubuntu and Ubuntu have the same kernel.

I observed the AC adapted bug, basically the system was not recognizing when the adapter was in/out and hence it was not switching Performance/Powersave mode. This bug was apparently also observed on some Ubuntu 9.04 machines.

Some people suggested a possible to work around the bug by recompiling the kernel with the ACPI loaded as module (or something). I downloaded the kernel source and recompiled the kernel using info from this link:

[http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/](http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/)

I followed all instructions, however, I changed the i386 to amd64 to get 64 bit support. During the "debian.master/scripts/misc/kernelconfig editconfig" section I hanged the ACPI thing from * to m, the CPU type from generic x64 to Core 2 Duo family and the default number of CPU supported from 64 to 32 (it is still an overkill).

This fixed the bug for me. Now the AC adapter is being detected properly. I have posted a link with the new kernel version, however, before you download you should know:

1. My knowledge of the Linux kernel consists of reading on-line how-tos and copy/paste from them to a command line.
2. I cannot provide any warranty or support, nor can/will system76 nor can/will Canonical (Canonical specifically make sit clear that they will void your support agreement if you use a recompiled kernel).
3. This may or may not work on your machine due to many reasons, which I am sure I cannot predict.
4. This may damage your system.
5. Downloading stuff from random people on the Internet is not a smart thing to do, when it comes to the kernel itself, this is tipple so.
6. I used kernel version 2.6.31-15.49 as basis, this version has not been tested (on that matter, I have not yet tested my laptop for all the features such as suspend/hibernate).
7. It would be more appropriate if system76 people come up with a kernel that is a temp fix until System76/Canonical/Kernel developers figure out the problem and fix it permanently.
8. It is possible that the fix was due to another feature introduced in kernel 2.6.31-15.49, everyone might have it officially fixed with the next kernel update and in fact my changes had no effect.

I am posting this so that you can use if:
1. Due to the bug, your system has become inoperable and your well being depends on it.
2. You like the adrenalin rush from doing extremely hazardous things.

To install: download, untar and install all the files. For me grub was automatically updated, however, I don't know if this is always the case.

Go to the directory where you downloaded the tar.gz file and do. Please remember that I warne you and I bare no responsibility for the consequences.

```

tar -xvf linux-core2-bugfix.tar.gz
sudo dpkg -i linux-*

```

[http://rapidshare.com/files/308052919/linux-core2-bugfix.tar.gz](http://rapidshare.com/files/308052919/linux-core2-bugfix.tar.gz)

---

### Post by HotShotDJ on 2009-11-17
I strongly advise against downloading kernels from unofficial sources... even sources with the best of intentions. ;)

Having said that, I've found a custom compiled kernel with CONFIG_ACPI_AC=m and CONFIG_ACPI_BATTERY=m improves power management in Ubuntu on my PanP5 -- but only by a small amount. However, it does not correct the problem with gnome power management failing to report the time left to fully discharged/fully charged.  I also compile the kernel with Core 2 Duo optimizations (CONFIG_MCORE2=y).  Again, just like with power management, the benefits, if any, are not noticeable by the user.

The website that the OP linked to is the very same site that I used for instructions.  It is very easy to follow the instructions and most people should be able to follow it without a problem.  If you'd like a custom kernel, please use those instructions.  Don't download anybody's personal kernel.

---

