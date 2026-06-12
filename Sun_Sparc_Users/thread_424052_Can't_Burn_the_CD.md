---
title: "Can't Burn the CD"
date: 2007-04-26
forum: Sun Sparc Users
---

### Post by deanna on 2007-04-26
Okay, I may be stupid here.....  But

I downloaded the Sparc ISO for Ubuntu but I can't burn the CD.  I suspect it's because I'm trying to burn from a CD.  Unfortunately I have no way of burning from the Sparc.  Is there any way I can get my hands on a CD?

Thanks,
Deanna

---

### Post by Delta_Farce on 2007-04-26
Hi,

When you say you're trying to burn from a CD, do you mean that you burnt the ISO file on to a CD?

If so, then what you should do is open you're burning program and select the option to burn a CD from an image file. If you can do that, just select the sparc iso file you have and it should create a new bootable ubuntu cd for your machine.

Hope this helps,

Mark

---

### Post by deanna on 2007-04-27
Okay, here's the problem -

The download is good, I checked the MD5 checksums and all is well.  I know how to burn an ISO - I've burned Ubuntu client for PCs many times.  But I try to burn the Sparc image, and I get the following:

This disc is incompatible with the source disc
Sense: 02  ASC: 04  ASCQ: 07 (Command 00)
-------------------------------------------------------
Px.dll: 3.2.40.500
pxafs.dll: 3.2.40.500
pxdrv.dll: 1.1.93.1
PxMas.dll: 3.2.40.500
pxsfs.dll: 3.2.40.500
PxWave.dll: 3.2.40.500
PXWMA.dll: 1.0.0.3


Now I'm using an XP system running Sonic Record Now version 7.  The CDs are 700MB.  As I said before I've burnt Ubuntu PC on the same system.  SO is there something with the Sparc image?  I've had a friend try to burn a CD too and he's had no luck either.

Thanks,
Deanna

---

### Post by erm67 on 2007-04-28
I also had problems burning the iso with nero so I resorted to cdrecord and it worked (probably because it is dumb and burns everything).
cdrecord -v speed=4 dev=/dev/whatever image_filename.iso
It worked then flawlessly.

---

