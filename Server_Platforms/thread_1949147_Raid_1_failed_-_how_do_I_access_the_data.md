---
title: "Raid 1 failed - how do I access the data?"
date: 2012-03-29
forum: Server Platforms
---

### Post by diefenic on 2012-03-29
Hi guys, I got a big problem
my ubuntu server was running on raid1, but it failed (no idea why) and now I'm not able to
access the data, I've tried, using live ubuntu and mdadm, access the partitions, but got no success

is there way to access the data?



thanks!

---

### Post by darkod on 2012-03-29
Since you mention mdadm I guess it was software raid.

By fail you mean completely, both disks? Raid1 should keep working with one disk too.

If I am not mistaken, you should be able to see the data even without mdadm, that's the beauty of software raid. mdadm keeps the raid together, but the information is readable by itself on raid1.

To start with, what does fdisk show about the disks?

---

### Post by diefenic on 2012-03-29
> **darkod said:**
> Since you mention mdadm I guess it was software raid.

By fail you mean completely, both disks? Raid1 should keep working with one disk too.

If I am not mistaken, you should be able to see the data even without mdadm, that's the beauty of software raid. mdadm keeps the raid together, but the information is readable by itself on raid1.

To start with, what does fdisk show about the disks?

fdisk shows me the sda1 partition(hard disk 1) and the sdb1 partition (hard disk 2) with "Linux raid autodetection", both disks work, but when i try to get raid information, seems that I don't have a raid system

---

### Post by rubylaser on 2012-03-29
> **darkod said:**
> Since you mention mdadm I guess it was software raid.

By fail you mean completely, both disks? Raid1 should keep working with one disk too.

If I am not mistaken, you should be able to see the data even without mdadm, that's the beauty of software raid. mdadm keeps the raid together, but the information is readable by itself on raid1.

To start with, what does fdisk show about the disks?

If it's mdadm, the individual disks should be able to be mounted and read from unless both disks failed at the same time.  fdisk -l is a good idea to get started.

---

### Post by darkod on 2012-03-29
And from live mode in terminal if you simply try:

sudo mount /dev/sda1 /mnt
ls /mnt

Can you see the data?

Rubylaser can correct me if I am wrong, he is the expert on raid. :)

---

### Post by diefenic on 2012-03-29
I tried sudo mount /dev/sda1 /mnt and sdb1 too.
both sda1 and sdb1 can't be mounted because their are detected as raid system

Also I tried some commands with mdadm to access data, without success

---

### Post by darkod on 2012-03-29
OK, google says you can do it, but only if you mount it as read-only. That would still allow you to copy data at least. It would be something like:
sudo mount -o ro -t ext4 /dev/sda1 /mnt

If you used ext3, change in the command.

If that works you can copy data to external hdd or similar.

Then you can continue trying to save this without reinstalling from scratch. Rubylaser can usually help a lot with this subject.

---

### Post by rubylaser on 2012-03-29
> **darkod said:**
> OK, google says you can do it, but only if you mount it as read-only. That would still allow you to copy data at least. It would be something like:
sudo mount -o ro -t ext4 /dev/sda1 /mnt

If you used ext3, change in the command.

If that works you can copy data to external hdd or similar.

Then you can continue trying to save this without reinstalling from scratch. Rubylaser can usually help a lot with this subject.
You're doing a great job :)

If you're running from a LiveCD, have you installed mdadm?  Then you can view the disks to see if they have superblock info on them.

```
sudo -i
apt-get update && apt-get -y install mdadm
mdadm -E /dev/sd[ab]1
```

If mdadm shows superblock info on either disk, you can even assemble the array in the LiveCD, but verify that both disks are good via smartmontools before you do anything but read from the array.

---

