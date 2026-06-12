---
title: "Encrypted partition performance problem"
date: 2008-08-05
forum: Server Platforms
---

### Post by MountainX on 2008-08-05
I read that the overhead of an encrypted partition in Linux was about 5%. I set up a server with two separate encrypted partitions. Copying a large number of files (GB's of data) from one encrypted partition to another is very slow and it maxes out all 4 CPUs (two Xeon dual cores). I wasn't expecting so much overhead.

The encrypted partitions are on two separate high-end hardware raid controllers. One uses RAID-5 and one uses RAID-0.

Copying from either encrypted partition to a non-encrypted partition seems to perform adequately and the CPU load is much lower (only one core shows significant load).

Running Hardy 8.4.1 amd64 
Dual Xeon with 6 GB RAM
LSI MegaRAID 320-2E SCSI controller with 4x Seagate 15k rpm Cheetahs.
Areca ARC-1220 SATA PCI-express 8x controller with SATA drives.

---

### Post by MountainX on 2008-08-05
I appreciate hearing any thoughts anyone has about why the data transfer is so slow and the CPU load is so high when copying from one encrypted drive to another. How could I gain deeper insights into the performance problem? Thanks.

EDIT: here is a link to one benchmark: [http://www.phoronix.com/scan.php?page=article&item=ubuntu_hdd_encrypt&num=3](http://www.phoronix.com/scan.php?page=article&item=ubuntu_hdd_encrypt&num=3)

---

### Post by MountainX on 2008-08-06
It is apparently not encryption... I think something else is causing poor disk performance.

I just found bug: [https://bugs.launchpad.net/ubuntu/+bug/216878](https://bugs.launchpad.net/ubuntu/+bug/216878)

I plan to make a new thread.

---

