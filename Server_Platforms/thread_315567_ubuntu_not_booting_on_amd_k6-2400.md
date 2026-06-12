---
title: "ubuntu not booting on amd k6-2/400"
date: 2006-12-09
forum: Server Platforms
---

### Post by ddaedalus on 2006-12-09
Hi,

I've set up a small server.

The hardware specs are:

- AMD K6-2/400
- Asus P5A, Aladdin 5 Chipset
- 512MB RAM
- Elsa Gladiac 2 32MB( simply a gf2 )
- IBM 10GB HD
- D-Link DWL-520
- Netgear FA310-Tx

Installing the Ubuntu-i386-server works flawless. After installation, it looks like the Linux-Kernel does not want to boot. Grub simply shows "Starting up..." and the computer reboots. But using the ubuntu-alternate/server-i386 version works.

thanks in advance
ddaedalus

---

### Post by CyberX on 2006-12-09
Hi.
There is a difference between Alternate and Server kernels. The Server CD kernel only works with i686 compatible processor (Intel Pentium Pro, Pentium II and later, or AMD K7 and later).
If you search in these forums you will find out to install with the  Server CD and replace the kernel before rebooting, but if you already have the Alternate CD installation working you have got pretty much the same thing.

---

### Post by ddaedalus on 2006-12-09
thanks, this clears things up.

---

### Post by stell86 on 2006-12-10
I had the same problem on older hardware - and couldn't find exactly how to replace the 386-kernel 'before installation ends', so I opted for installing the 5.10 server and then do a 'dist-upgrade' and then install my services.
See my post here: [http://ubuntuforums.org/showthread.php?t=315705](http://ubuntuforums.org/showthread.php?t=315705)on how I did it.

My installation was done yesterday.

HTH

---

