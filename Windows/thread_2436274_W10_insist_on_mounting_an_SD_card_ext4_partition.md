---
title: "W10 insist on mounting an SD card ext4 partition"
date: 2020-02-03
forum: Windows
---

### Post by hk42 on 2020-02-03
I'm using a disk-less mini PC.
First W10 was on the 64GB EMMC .
I used a 64GB sdcard in NTFS and assigned it letter E in W10.
To try Ubuntu I splitted The EMMC to make a 20GB ext4 partition.
For good measure I also splitted the SD card. It's second 20GB ext4 partition is mounted as /home.
Every thing is OK on the Linux side.
But for some reason W10 affects the letter E to the ext4 partition of the SD card and tells that a format is needed.
It refuses to ignore the partition and free letter E so that I can mount The NTFS sd card partition where it should be.
The only way I found to free letter E was to boot W10 with 2 USB dongles and un-mount them later. 
Is this another bug or am I missing something ?

---

### Post by yancek on 2020-02-03
A solution to your windows problem would probably have  a better chance of being resolved at a windows forum.  A default windows doesn't recognize and can't read/write to a Linux filesystem  Additionally, windows does not as a matter of course use drive letter on Linux partitions.  Probably sees the filesystem is not a windows filesystem and therefore suggests formatting.

---

