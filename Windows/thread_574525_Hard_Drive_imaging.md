---
title: "Hard Drive imaging"
date: 2007-10-12
forum: Windows
---

### Post by Jem00 on 2007-10-12
Hey guys,

I heard of imaging a hard drive on windows...
How would i go about doing this?

Because I usually make a mess of my windows..not that its hard to do...

Any help would be welcomed,

Thanks,

Jeremy.

---

### Post by asmoore82 on 2007-10-12
[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

---

### Post by Jem00 on 2007-10-12
Thanks

---

### Post by Xenaco on 2007-10-13
The ***dd*** command can be used to create an image of a disk or a partition.

I use it to create disk images by connecting an external hard disk to a system with USB or eSATA.

Enter the command:
[B][I]
dd if=/dev/[hdx or sdx] of=/dev/sdx bs=1024k[/I][/B]

use hda or sdb or sdb2 or whatever the device name of your source and destination drives.  if=source drive of=destination drive

[COLOR="DarkRed"][B]
BE VERY CAREFUL!!![/COLOR][/B] Screwing up your drive designations may wipe out your original disk information.  You may want to create a shell script so you don't have to re-enter this command and introduce additional chance for errors.

This command will copy disk partition and format information as it does a bit-for-bit copy the drive (errors and all if any on the source drive).

Be sure that your destination drive is as large or larger than the source drive.  If dd runs out of space on the destination drive before you have copied the source drive you will not get a complete copy. Any and all content which exists on the destination drive will be overwritten by the source data.

---

### Post by kulturloseramerikaner on 2007-10-13
I used dd just last night actually do clone my XP partition.  It took 7.5 hours to do 160GB, and it didn't give you a pretty statusbar or anything, but it made a perfect copy of XP on a USB hd.

---

