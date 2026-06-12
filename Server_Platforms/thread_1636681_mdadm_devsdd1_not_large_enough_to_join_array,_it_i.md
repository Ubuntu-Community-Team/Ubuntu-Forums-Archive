---
title: "mdadm: /dev/sdd1 not large enough to join array, it is a same-size disk though"
date: 2010-12-03
forum: Server Platforms
---

### Post by tyfius on 2010-12-03
When I set up my server during the summer I used the partitioning tool from the installer (10.04) to set up a RAID-5 containing 3 2TB disks.

I wanted to add two more disks today, but received the following error after formatting them as a primary partition (ext4) with gparted. (Also occurs with fdisk.)

```
$ sudo mdadm --add /dev/md0 /dev/sdd1
mdadm: /dev/sdd1 not large enough to join array
```

When I check sizes I get something like:
```
$ sudo sfdisk -s /dev/sda1 
1953513472
$ sudo sfdisk -s /dev/sdd1 
1953512001

```

So it looks like there's a difference. What can I do to solve this?

---

### Post by tyfius on 2010-12-03
I think I might have solved it by doing
```
sudo mdadm /dev/md0 --add /dev/sdd
```

It's doing something now, see how it goes.

---

### Post by dtfinch on 2010-12-03
For later on, keep in mind the partition /dev/sdd1 no longer exists since you added the full disk to the raid instead of just the partition.

Gparted aligns partitions to 1mb by default, at a small cost of space, but so do the Ubuntu installers since Lucid, so it should have been the same unless the old disks were already pre-partitioned some other way when you started.

I purposely make my raid partitions a little smaller than the max in case I encounter a drive that's slightly smaller than what I started with, but I've never actually seen that happen.

Out of curiosity, shat does sfdisk report for the sizes of the full disks /dev/sda and /dev/sdd?

---

