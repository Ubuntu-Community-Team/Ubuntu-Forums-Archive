---
title: "LVM No Valid Partition Table after upgrade"
date: 2012-07-13
forum: Server Platforms
---

### Post by Deronius on 2012-07-13
I set up my home server to use LVM for partitions / volumes in hopes that I would get more comfortable with things.  Until yesterday everything was going along fine and dandy.  For a couple of years actually.  I decided my 9.10 version needed to be upgraded.  The upgrade to 10 was fine then I decided to upgrade to 12.  Now I have to boot into recovery and all of my LVM volumes will not mount unless I tell them explicitly to including the root volume (the volume I originally had as root).  lvscan, pvscan seem to see everything okay.  When I do fdisk -l I see the partitions but each one has a "No valid partition table" line. Do I need to reassign these volumes?  If so, could someone remind me how to do that and how can I do that for the root volume?  

Sorry if this has been covered.  I see some posts out there but I haven't found a completely solved one.

Thanks.:confused:

---

### Post by darkod on 2012-07-13
If you mount your root LV for example at /mnt, and then open /mnt/etc/fstab, what does it show?

The No Partition Table doesn't necessarily mean a big problem. I think fdisk can't see "inside" the LVM so it gives that message for the LV volumes.

The disks it should see all right on the other hand.

You can also check what parted says:
sudo parted -l

Maybe only your /etc/fstab needs modifying so that it boots OK.

---

