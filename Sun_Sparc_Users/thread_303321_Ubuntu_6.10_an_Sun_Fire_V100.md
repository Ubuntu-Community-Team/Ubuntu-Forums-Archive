---
title: "Ubuntu 6.10 an Sun Fire V100"
date: 2006-11-20
forum: Sun Sparc Users
---

### Post by mklein on 2006-11-20
Hi,

I tried to install Ubuntu 6.10 on my Fire V100. But with cdrom install I got an PCI resource error after booting the install system.

I also tried network based install. It runs much better than cdrom install but it stops after detecting the hardware.

Does anybody get a working installation of Ubuntu with a V100?

MfG

Markus

---

### Post by can2002 on 2006-11-21
Hi Markus,

I went through exactly the same process last week for the first time and had the same message.

I did some trawling and found an entry for a Sun Blade 100 suggesting appending ide=nodma at the silo prompt (e.g. Linux ide=nodma).  This allowed me to complete the installation.  I also had to edit silo.conf in /boot to be able to subsequently boot, as follows:

image=/vmlinuz
        label=Linux
        append="ide=nodma"
        initrd=/initrd.img

Cheers,
Chris

---

