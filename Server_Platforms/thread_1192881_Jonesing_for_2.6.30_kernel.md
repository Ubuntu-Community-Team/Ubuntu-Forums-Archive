---
title: "Jonesing for 2.6.30 kernel"
date: 2009-06-20
forum: Server Platforms
---

### Post by Vegan on 2009-06-20
I am using 9.04 with updates. I noticed over on Linux.org that 2.6.30 is stable. I was wondering when that was going to be available to Ubuntu users?

---

### Post by Bachstelze on 2009-06-20
> **Vegan said:**
> I am using 9.04 with updates. I noticed over on Linux.org that 2.6.30 is stable. I was wondering when that was going to be available to Ubuntu users?

In the next release.

---

### Post by RD1 on 2009-06-20
I've been using it here since the day it became available. Working great! No splash during boot though.

---

### Post by ptn107 on 2009-06-20
If you want it you can get it here.  You will need all three packages for your architecture:

32 bit:
[U][linux-headers-2.6.30-020630_2.6.30-020630_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb")
[linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb")
[linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb")[/U]

64-bit:
[U][linux-headers-2.6.30-020630_2.6.30-020630_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb")
[linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb")
[linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb")[/U]

Save them to your home folder, pop open a terminal and type:
```
sudo dpkg -i *.deb
```
then reboot.

---

### Post by windependence on 2009-06-21
> **Vegan said:**
> I am using 9.04 with updates. I noticed over on Linux.org that 2.6.30 is stable. I was wondering when that was going to be available to Ubuntu users?

But why? Not necessary and probably buggy.

-Tim

---

### Post by Vegan on 2009-06-26
> **ptn107 said:**
> If you want it you can get it here.  You will need all three packages for your architecture:

32 bit:
[U][linux-headers-2.6.30-020630_2.6.30-020630_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb")
[linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb")
[linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb")[/U]

64-bit:
[U][linux-headers-2.6.30-020630_2.6.30-020630_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb")
[linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb")
[linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb")[/U]

Save them to your home folder, pop open a terminal and type:
```
sudo dpkg -i *.deb
```
then reboot.

Thanks, works fine for my basic LAMP stack + development tools

---

### Post by RD1 on 2009-06-26
> But why? Not necessary and probably buggy.


Improved video performance (at least on my laptop with intel video) and my webcam works!

---

### Post by Vegan on 2009-07-17
I noticed today on the net that a security defect has been found but its only a problem as its only local-host linked.

At least I am happy to see there are lots of people checking the code for problems.

---

