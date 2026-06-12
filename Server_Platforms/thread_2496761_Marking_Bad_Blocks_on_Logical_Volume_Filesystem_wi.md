---
title: "Marking Bad Blocks on Logical Volume Filesystem with Multiple Physical Volumes"
date: 2024-04-11
forum: Server Platforms
---

### Post by pogo7 on 2024-04-11
Hey everyone,


I've encountered a situation where I needed to mark bad blocks on a _**ext4**_ - Logical Volume (LV) filesystem that spans multiple Physical Volumes (PVs) within a Volume Group (VG). I wanted to share my approach and confirm if it's the correct way to handle this scenario.


I have a setup where my LV spans across two HDDs (sda and sdc) within a VG.
One of the HDDs (sda) has bad blocks that need to be marked to prevent data corruption.

Approach:

Identify Bad Blocks:

I used the badblocks command to scan the HDD (sda) and generated a list of bad blocks.
Command:

```
sudo badblocks -sv /dev/sda > badblocks_sda.txt
```     (would -w be beneficial?)


Mark Bad Blocks on LV filesystem:


After obtaining the list of bad blocks, I use fsck -l to mark them on the LV filesystem.

Command: 

```
sudo fsck -l badblocks.txt /dev/nfs_dir_vg/nfs_dir_lv
```

Questions:


Does this approach correctly mark bad blocks on the LV filesystem spanning multiple PV?
Are there any potential pitfalls or better approaches to handle this scenario?
I would appreciate any insights or feedback on this approach. Thank you!

---

