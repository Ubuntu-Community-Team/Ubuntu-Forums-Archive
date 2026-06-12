---
title: "mdadm with mixed sector sizes"
date: 2011-03-29
forum: Server Platforms
---

### Post by AvidElite on 2011-03-29
Ubuntu Server 9.10

I've got an mdadm software raid5 made of four 2TB drives.  They're WD20EADS drives, so they use the old 512-byte sectors.  I need to extend the raid, but I can't find a sure answer if I could reshape onto a drive with 4K sector sizes.

In short, if I have a raid5 built on four 512b sector drives, can I reshape the raid to continue using those four drives, and add a fifth drive (same capacity) that uses the new 4K sectors?

Thanks in advance,

Adam

---

### Post by rubylaser on 2011-03-29
That should work as long as you partition the drive to align to the 4K sectors.  You might lose a far KB of space across your array due to aligning the partition, but it should work.  I don't have any Advanced Format drives, or I'd be happy to test for you.

---

### Post by AvidElite on 2011-03-29
rubylaser,

I actually don't use partitions, I let mdadm just mount /dev/sdb through /dev/sde.  Will that matter?

I'm given to understand that since mdadm is laying the raid structure directly on the disc without containing it in a partition I should be safe, but this is pretty mission critical and I want to get second and third opinions.

Unfortunately I don't have spare drives to test with, or a place to back up the data (5tb is a lot to back up!).

I certainly appreciate anyone knowledge on this.

---

### Post by rubylaser on 2011-03-29
Without using partitions on the Advanced Format drive, your sectors won't be aligned, so performance can suffer by as much as 30%. I'd probably want to avoid that much of a slow down myself.

---

