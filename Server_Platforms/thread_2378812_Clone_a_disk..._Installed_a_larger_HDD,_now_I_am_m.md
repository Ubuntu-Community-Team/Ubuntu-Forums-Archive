---
title: "Clone a disk... Installed a larger HDD, now I am missing half the size of the new HDD"
date: 2017-11-27
forum: Server Platforms
---

### Post by bryang4 on 2017-11-27
Hello all,
I have a laptop with Ubuntu Server 17.04 installed.  I HAD a 500 GB HDD drive in it.  I used clonezilla to go from that 500 GB HDD to a 1TB.  Now when I do a df -h , I can only see 500 GB available to me, even though i have installed a 1000 GB drive...  What have I done wrong? 

Any help is appreciated! thanks!

---

### Post by QIII on 2017-11-27
Hello!

When you cloned it, you should not have gotten just data, but also the partition table with its definitions.  My guess is that if you looked at the table with gparted (assuming it's not LVM) you would see your previous partitions at the same size and about 500GB of unallocated space.

---

### Post by darkod on 2017-11-28
Cloning a disk completely usually includes the partition table. Because in the table on the old disk it said you have partitions occupying 500GB, with cloning the table on the new disk says the same. It doesn't care that the disk is actually 1TB. The second half is unpartitioned space...

You can try extending the partition but that can only work if there is no other partition behind it (and swap might be behind the root partition).

You can also try the cloning again but on partition level, not the whole disk. Create new big partition on the new disk and then clone the partition of interest from the old to the new one, which will not clone the partition table contents.

---

### Post by mastablasta on 2017-11-28
or you can add a partition in the empty disk space.

but clone is clone - 1:1

it should be easy to expand partition to full space (you might need to turn off swap and move it if it really is the last one.).

---

