---
title: "MDADM, partitions and formatting Q:"
date: 2011-10-10
forum: Server Platforms
---

### Post by Krupski on 2011-10-10
Hi all,

I'm running Ubuntu 11.04 64 bit server in a home file server and using MDADM to provide a RAID-6 array.

I recently backed up my data and changed around the configuration of the server (put in larger HDD's).

Anyway, after starting the new array, I formatted (using EXT4) the /dev/md0 device directly... no partition. And it worked. And it works just fine.

So my question is... is a partition even necessary? Is there any functional difference?

Thanks...

-- Roger

---

### Post by rubylaser on 2011-10-11
If you're going to use the array, there is no reason for a partition.  Putting the filesystem right on top of mdadm is the correct way to do it.

---

### Post by Krupski on 2011-10-11
> **rubylaser said:**
> If you're going to use the array, there is no reason for a partition.  Putting the filesystem right on top of mdadm is the correct way to do it.

Thanks for the reply. What are your thoughts on doing the same for a single disk (i.e. mkfs.xxx /dev/sda)? Is there any need to make a /dev/sda1 partition?

-- Roger

---

### Post by rubylaser on 2011-10-11
On individual disks mkfs is usually on a disk partition.  For administration's sake it would be good practice to create a partition, and put your filesystem on top of it.

---

