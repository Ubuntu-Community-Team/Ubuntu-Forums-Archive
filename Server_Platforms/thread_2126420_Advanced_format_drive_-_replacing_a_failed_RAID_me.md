---
title: "Advanced format drive - replacing a failed RAID member"
date: 2013-03-17
forum: Server Platforms
---

### Post by MakOwner on 2013-03-17
I have an 8 disk array of Seagate 1.5TB 5900 "green" drives.
I had one go bad and Seagate replaced it under warranty.

The drive I got as a replacement was an "Advanced Format" drive.

```

Old drive: 
Model Family:     Seagate Barracuda LP
Serial Number:    9XW05B85
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
 
New drive:
Model Family:     Seagate Barracuda Green (Adv. Format)
Serial Number:    6YD05MN6
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0


```


The block counts were slightly different on the drives - the new one was slightly larger.
I used sfdisk to duplicate the partitons from another drive and added it to the array.  
It's just a few minutes away from rebuilding.

How much if any problems will this different format drive cause me?

---

### Post by rubylaser on 2013-03-17
Since you used sfdisk and copied the partition table over from the previous setup, this will work great :)  This is exactly the reason I recommend to use partitions vs. the whole disk for mdadm  (it's also nice to be able to properly align the partition).

---

