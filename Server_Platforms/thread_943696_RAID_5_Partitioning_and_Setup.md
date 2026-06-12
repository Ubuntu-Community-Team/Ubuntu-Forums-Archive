---
title: "RAID 5 Partitioning and Setup"
date: 2008-10-10
forum: Server Platforms
---

### Post by jdholifield on 2008-10-10
I have a server with 4 250GB hot swappable hard drives.  Right now I have 1 drive partitioned as /boot, /swap, /, and /var, and I have the other 3 drives configured as RAID5 and mounted to /usr .

Basically everything is working, but have a few issues and would like to rebuild this machine as 8.04 LTS.

If I rebuild this machine, is there any way at all that I can get all 4 drives partitioned and mounted as RAID5 ?

When I built this machine a couple years ago, I struggled with trying to get all 4 drives in the RAID, and eventually gave up and went with what I have now - OS installed on one drive, the other 3 dedicated to RAID.

Is it possible for me to get all 4 drives configured as RAID5, or will I just be setting myself up for frustration and defeat if I attempt this ?

---

### Post by fjgaude on 2008-10-11
When you think about it you can't boot from a software raid5, because the whole kernel and other files are stripped acroos each drive of the array.

You can use raid1 and boot from that.

I've never tried other than whole disk arrays, no partitions.

---

