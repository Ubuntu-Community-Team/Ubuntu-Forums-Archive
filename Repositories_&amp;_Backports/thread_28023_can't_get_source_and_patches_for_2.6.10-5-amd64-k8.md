---
title: "can't get source and patches for 2.6.10-5-amd64-k8"
date: 2005-04-18
forum: Repositories &amp; Backports
---

### Post by harbaugh on 2005-04-18
Hi-

I have attempted to follow the guides
  [http://www.ubuntulinux.org/wiki/KernelBuildpackageDetailedHowto](http://www.ubuntulinux.org/wiki/KernelBuildpackageDetailedHowto)
and
  [http://www.ubuntulinux.org/wiki/KernelByHandHowto](http://www.ubuntulinux.org/wiki/KernelByHandHowto)

in order to download the latest 2.6.10 kernel source and patches,
ideally specific to amd64-k8.   I would like to rebuild the kernel
that I have installed, which is linux-image-2.6.10-5-amd64-k8.
However, no matter what I do, I can't seem to download the right
source and patches so that
  /usr/src/linux-source-2.6.10-2.6.10/debian/config/amd64/amd64-k8
matches my installed kernel:

$ diff /usr/src/linux-source-2.6.10-2.6.10/debian/config/amd64/amd64-k8 /boot/config-2.6.10-5-amd64-k8 |head
3,4c3,4
< # Linux kernel version: 2.6.10-1-amd64-k8
< # Tue Dec 28 15:15:46 2004
---
> # Linux kernel version: 2.6.10-5-amd64-k8
> # Tue Apr  5 12:09:59 2005
34a35
> # CONFIG_AUDITSYSCALL is not set
85a87
> CONFIG_X86_MCE_INTEL=y

What are the correct steps to get the patched source to rebuild
linux-image-2.6.10-5-amd64-k8?

Thanks,
Toni

---

### Post by az on 2005-04-18
Have you done an update in synatic?  It would seem that you have an older version of the source:

Linux kernel version: 2.6.10-1-amd64-k8

Linux kernel version: 2.6.10-5-amd64-k8


Did you install linux-tree?

---

### Post by harbaugh on 2005-04-18
I don't use synaptic, I use apt-get directly.  Before I attempted anything,
I did a

  apt-get update

to make sure my cache was up to date.  According to dpkg, I have the latest
2.6.10 source:

$ dpkg -l | grep linux-source
ii  linux-source-2.6.10             2.6.10-34                       Linux kernel source for version 2.6.10 with Ubuntu patches

This matches the latest image that I have installed:

$ dpkg -l | grep linux-image
ii  linux-image-2.6.10-4-amd64-gene 2.6.10-25                       Linux kernel image for version 2.6.10 on x86_64.
ii  linux-image-2.6.10-4-amd64-k8   2.6.10-25                       Linux kernel image for version 2.6.10 on AMD K8.
ii  linux-image-2.6.10-5-amd64-k8   2.6.10-34                       Linux kernel image for version 2.6.10 on AMD K8.
ii  linux-image-amd64-k8            2.6.10-7                        Linux kernel image on AMD K8.

Unfortunately, the config file in the latest source package does not match
the config file in the latest image for my platform.  What package do I have
to get in order to get the 'true' latest source?

Thanks again,
Toni

---

### Post by az on 2005-04-18
linux-tree?

---

### Post by harbaugh on 2005-04-18
$ dpkg -l | grep linux-tree
ii  linux-tree                      2.6.10-7                        Linux kernel tree for building prepackaged Ubuntu kernel images
ii  linux-tree-2.6.10               2.6.10-34                       Linux kernel tree for building prepackaged Ubuntu kernel images

---

