---
title: "LVM snapshot question/help"
date: 2015-11-18
forum: Server Platforms
---

### Post by m0rph3us0306 on 2015-11-18
Im sure I am missing one stupid little thing, but our psql database is around 1T spanned across 2 disks.  Full backups are taking a long time, so it was suggested to do an LVM snapshot.  I am reading where some are saying that it's not a backup, but others say you can take that image, mount it, etc. so the first question is just that, is an LVM snapshot a good full backup of an LVM disk?

*note, this is in amazon's AWS so adding disks to play is really simple*

I added a 500G disk, added it to the volume group, then tried to create the snapshot;
```
lvcreate -L 400G -s -n db.snap /dev/DB/DataBase
```  and getting an error;
Insufficient free extents in volume group, 128000 required.

From my initial thought if I had a 1T database, when you setup the snapshot I would need at least 1T, but then the more I read, it seems the snapshot is more of a point in time and just writes the changes.  Am I correct in that?   The examples always showed a small snapshot size when creating but I am just really confused.  Even made the mistake of adding 1T to the logical volume with the database with an lvmextend and resize, so now I have an extra 1T I need to figure out how to remove.

So, back to the original, basic questions;

1.  Should an LVM snapshot be used as a full database backup.
2.  Does the -s snapshot have to be at least equal size to the disk.
3. Is the above syntax correct as I didn't see a place to say create the snapshot of this logical volume - /dev/DB/DataBase AND put it here.  Does it just use the same volume group /dev/DB which should have the free space available in the group (just not allocated to a logical volume)
4.  Best way to reduce an lvm volume and actually remove a disk (knowing there is enough space), is the system smart enough to say let me start by removing the disk not in use.


Thanks all.

---

### Post by darkod on 2015-11-18
Lets talk about that "new" disk first. I will need to read up on my LVM knowledge to try and answer the rest.

DO NOT simply remove the disk! Once you extended the LVM over it, it is possibly being used, so simply removing it will break the LVM... There is a way to shrink the LV, and the removal of the "physical" disk is the last step. We just have to search and double check the best commands to use.

The process goes like:
1. Shrink the filesystem first.
2. Shrink the LV.
3. Remove the PV from the VG.
4. Remove the disk.

---

### Post by darkod on 2015-11-18
I know this is from redhat documentation but it seems to show detailed steps for what you want. And LVM works the same on ubuntu...
[https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/5/html/Logical_Volume_Manager_Administration/disk_remove_ex.html](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/5/html/Logical_Volume_Manager_Administration/disk_remove_ex.html)

How does that look to you?

---

### Post by m0rph3us0306 on 2015-11-18
Looks pretty darn accurate.   I just kicked off a backup "just in case", which will take a while.  In the meantime I am going to play on a VM a bit adding, removing and will post back something most likely tomorrow after all is said and done.

Stay tuned, and timing was perfect as I just got in!

Thanks again

---

