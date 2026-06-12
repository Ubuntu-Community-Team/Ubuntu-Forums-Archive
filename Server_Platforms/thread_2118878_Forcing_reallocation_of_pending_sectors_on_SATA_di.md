---
title: "Forcing reallocation of pending sectors on SATA disks in a software RAID volume"
date: 2013-02-22
forum: Server Platforms
---

### Post by MakOwner on 2013-02-22
I have an 8 disk software RAID 5 array and one of the disks is reporting a high reallocated sector count and some pending sectors.

I have used the method described here to force reallocation of pending sectors on drives used as single drives in the past.

[http://timelordz.com/wiki/SMART_Rewriting_Bad_Sectors](http://timelordz.com/wiki/SMART_Rewriting_Bad_Sectors)

This method describes doing this using the files systme block size as part of the calculation -- since there is no (complete) files system on this disk, is it safe to calculate the location of the bad sector using the block size of the file system built on the array?

Anyone have any experience doing this on a disk in softare RAID array?

---

### Post by SaturnusDJ on 2013-02-22
An interesting question! I think you can not do the same because the filesystem is spread over multiple disks.
Raid1 might be an exception because I've seen such a disk is also mountable as single disk.

---

### Post by Vegan on 2013-02-22
get a new larger disk and backup your files, then break the array.

you can then run disk checks etc and see if the disk is able to correct itself or whether its exhausted its supply of spare sectors.

---

### Post by SaturnusDJ on 2013-03-01
Edit: wrong topic.

---

### Post by MakOwner on 2013-03-01
I just finished duplicating all fo the data to another array and I'll use my standby drive to swap out the drive in the array.
Once I yank the drive, I'll attach it to a controller in another machine as a single disk and try a zero-fill over the entire disk.

I ran across a read error as I was copying data off the array -- near as I can tell the RAID compensated for the bad sectors and didn't result in a bad copy, but the logs looked pretty nasty.
And the reallocated sector count is rising on that drive ...

---

