---
title: "Setting up RAID5 - where to put /boot?"
date: 2015-11-22
forum: Server Platforms
---

### Post by honeycombs_big_yahyahyah on 2015-11-22
Hi Folks,

Just building a new machine with 4 identical 3TB seagate SATA HDD's - plan to install ubuntu server 14.04.  My original plan was to put all 4 drives into a RAID5, but now reading that /boot can't be in the array.  So, what is the best approach?  Make a small /boot partition on one of the drives, and if that drive happens to die, then live with it?  Put /boot on a USB drive perhaps, allowing all 4 drives to be fully integrated into RAID5?  I can't add another HDD, as the motherboard only has 4 SATA ports.

Any thoughts very welcome.

Thanks!

---

### Post by darkod on 2015-11-22
What you could do is make a raid1 array of 4 partitions for /boot. Or for the whole / partition (not to have separate /boot). But if you make the / "smaller" (not on the big array), make sure you plan the usage you need. For example, if you need much space on /var, make the /var on the big array and / on a smaller array.

On my home server I also have 4 disks and I have a 32GB raid1 array for /. The rest is a big array for /data (you can create any mount point you want).

If you do create a smaller array only for /boot, don't make it too big. A size of 2GB is enough.

That way you are protected if any disk fails, because you have /boot (or root) on all 4 disks.

---

