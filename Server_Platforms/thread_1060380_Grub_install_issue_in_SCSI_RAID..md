---
title: "Grub install issue in SCSI RAID."
date: 2009-02-04
forum: Server Platforms
---

### Post by dmovad on 2009-02-04
I am trying to install ubuntu server edition 8.04 on an Intel server with an Intel motherboard SE7520AF2. This motherboard supports SCSI RAID 1 and I have 2 Fujitsu MAX3147NP 147GB u320 15K Ultra320 SCSI drives paired for installation of the operating system.  After going through the install a couple of times and never being able to boot from the hard drives I tried a reinstall where I placed just the /boot partition on a SATA drive and the balance of the OS and programs on the SCSI RAID and now the system boos just fine.  Note that when I had issues installing the entire OS and /boot on the SCSI RAID I also tried to reinstall grub and was never successful getting the system to boot entirely from the SCSI RAID.  Now I have a working system however it seems like a half *** install with the /boot partition on a separate drive where I never intended it to be.  Needless to say I'd rather have the entire OS including the /boot partition on the SCSI RAID.  Note this RAID is on the Motherboard and is controlled by the BIOS (invisible to the OS).

If anyone has a clue as to why this install fails and how to fix it I'd be grateful.

Thanks...

---

### Post by fjgaude on 2009-02-04
It seems you are trying to use the BIOS fakeRAID without a driver for Ubuntu OS. This cannot work.

You might look into using a program called dmraid that would permit you to mount whatever is placed on the raid1 array, or consider this:

[http://radu.rendec.ines.ro/howto/raid1.html](http://radu.rendec.ines.ro/howto/raid1.html)

and this:

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

Good luck!

---

### Post by dmovad on 2009-03-22
I did finally resolve the issue preventing me from having Ubuntu 8.04 successfully boot.  I tried again to install Ubuntu 8.04 the other day and noted when I received the Grub error 17 that Grub was trying to boot from (hd1,0) when in fact the boot partition was on "hd0,0).  Once I edited the "/boot/grub/menu.lst" and corrected the boot partition to "hd0,0" Ubuntu successfully booted.  A small but very important thing to have missed on my part.

---

### Post by fjgaude on 2009-03-22
Well, it is easy to miss things when there are so many to handle to get everything just right... happy you found your problem.

---

