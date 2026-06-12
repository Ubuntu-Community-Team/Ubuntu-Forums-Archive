---
title: "Ubuntu Server 7.04 RAID1 Sil680"
date: 2007-05-11
forum: Server Platforms
---

### Post by ka1wcc on 2007-05-11
I have installed the 7.04-server with raid1 and a Sil680 controller. no errors doing installation.
it wont root of my HD.

Do I need to compile a new kernel with SIL680 and RAID support?

---

### Post by craigp84 on 2007-05-12
Probably not, this controller should be supported out the box.

Do you have any IDE hard drives in your system as well? Or is it only the SATA disk connected to this controller?

Reason i ask is just the way linux enumerates devices at startup, coupled with the way Ubuntu creates /etc/fstab, means that it fails to boot in certain situations because it's looking at the wrong disk.

Otherwise, it's most likely to be a failure to install the grub stuff properly.

Boot off the install CD, get as far as the "configure your network interfaces" bit - but don't go any further. Then ALT+F2 onto the console, then do:

mount -o bind /proc /target/proc
mount -o bind /dev /target/dev
chroot /target /bin/bash
mount -a     # mounts any other partitions such as /var etc. if you've set it up that way

grub-install /dev/sda

grub
grub> device (hd0) /dev/sdb
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

Note the "device (hd0) /dev/sdb" line, sounds counter intuitive huh? We do it that way because if sda goes away, suddenly sdb is (hd0) to grub, and so the config then makes sense.

Hope this helps,

Craig

---

