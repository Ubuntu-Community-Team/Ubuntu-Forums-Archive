---
title: "Is XFS supported as the root file system on Ubuntu 18.04?"
date: 2019-06-06
forum: Server Platforms
---

### Post by JoyceBabu on 2019-06-06
Does Ubuntu Server 18.04 support XFS for the root filesystem? The Ubuntu wiki says

> GRUB-Support is in an early stage, therefore using xfs as boot-filesystem can be a bad idea

I plan to use a separate 1GB ext4 partition for /boot. Since all other filesystems are mounted on the root filesystem, will an XFS root affect grub?

---

### Post by SeijiSensei on 2019-06-06
No, it won't affect grub.

If you use XFS, make sure you have a good uninterruptible power supply. I tried XFS at one point and any power disruptions would cause data loss. 

Why not just use ext4?

---

### Post by JoyceBabu on 2019-06-06
> No, it won't affect grub.

Thank you for the information.

> If you use XFS, make sure you have a good uninterruptible power supply. I tried XFS at one point and any power disruptions would cause data loss. 

The disks are configured in hardware raid controller with BBU.

> Why not just use ext4?
I have been reading reviews about the performance of XFS compared to EXT4, and read that XFS works better, in case of RAID10, due to parallel IO.

---

