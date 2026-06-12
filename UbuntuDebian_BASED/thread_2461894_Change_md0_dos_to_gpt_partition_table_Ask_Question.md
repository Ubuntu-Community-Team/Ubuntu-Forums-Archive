---
title: "Change md0 dos to gpt partition table Ask Question"
date: 2021-05-09
forum: Ubuntu/Debian BASED
---

### Post by gus_zernial on 2021-05-09
On a kde neon system, I had a drive failure of one drive on an mdadm two drive (non-boot) RAID1 mirrored array. After some trials and tribulations, I managed to replace the failed drive with an identical new drive and resync successfully.

The RAID1 mirrors two 4GB drives, both with GPT partition tables, but for some reason if I run $sudo fdisk /dev/md0 I now get the warning: "The size of this disk is 3.7 TiB (4000650690560 bytes). DOS partition table format cannot be used on drives for volumes larger than 2199023255040 bytes for 512-byte sectors. Use GUID partition table format (GPT)."

Is it possible to convert the md0 array from dos to gpt partition table without losing data? What are the steps/commands to do so?

---

### Post by coffeecat on 2021-05-10
*Thread moved to **Ubuntu/Debian Based** sub-forum.*

---

