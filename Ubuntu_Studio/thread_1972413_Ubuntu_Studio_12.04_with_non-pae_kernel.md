---
title: "Ubuntu Studio 12.04 with non-pae kernel?"
date: 2012-05-03
forum: Ubuntu Studio
---

### Post by raydar on 2012-05-03
When attempting install Ubuntu Studio 12.04 from DVD (on a Dell Inspiron 9200, with a 32-bit Pentium M 725 processor and 2GB RAM), I received the message 
> This kernel requires the following features not present on the cpu:
pae
Unable to boot - please use a kernel appropriate for your cpu.
and was unable to proceed.

The problem is discussed in the Ubuntu forums regarding Ubuntu and its variants in general at [http://ubuntuforums.org/showthread.php?t=1959675]("http://ubuntuforums.org/showthread.php?t=1959675"), but I've found no mention of whether there is a non-PAE version of the realtime or low-latency kernels for Ubuntu Studio 12.04. 

Is there an option I can choose in the live installer menu that will help (I bet not)?  Alternatively, perhaps someone has created a version of the Ubuntu Studio 12.04 DVD ISO with a non-PAE version of the kernel?  (I'd love to do it myself, but I barely know how to compile software, let alone modify a kernel.)

---

### Post by Cheesemill on 2012-05-03
You could always install with the non-PAE version of the mini ISO and then install all of the ubuntustudio-* packages.

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/)

---

