---
title: "booting with no cd driver"
date: 2006-02-27
forum: Server Platforms
---

### Post by cktheman on 2006-02-27
I installed Ubuntu and I'm using it as a web server.
All worked until I phisically disconnected CD-ROM driver. I wish to remove it before sending the server for housing.
Whwn I boot without CD-ROM driver it takes 15 minutes waiting for the kernel to start.
can anyone help me?
thx

---

### Post by stuporglue on 2006-02-27
Once it's booted, try editing /etc/fstab and commenting out the /dev/cdrom line. Maybe that'll work.

---

### Post by cktheman on 2006-02-28
Thx for the help.. unfortunately it doesn't work.. by file is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
#/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

if I boot verbously I see that it is trying to access HDA with no success

---

