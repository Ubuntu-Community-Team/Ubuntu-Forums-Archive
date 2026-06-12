---
title: "how do i mount something on my raid disks"
date: 2020-08-19
forum: Server Platforms
---

### Post by math492m on 2020-08-19
hi im running the following raid 10 configuration 
4 main 2tb hdds 
and 1 spare 2tb hdd 

how do i mount /backup on the array

---

### Post by TheFu on 2020-08-19
Huh?

RAID isn't mounted.  The file system is mounted.  Do you have a file system?

Also, backups probably shouldn't be wasted on a RAID10 setup.  RAID is for HA ... backups aren't the important part.  Use RAID on the real disks, not backup storage.

What sort of RAID is it?  Fake-RAID, SW-RAID, HW-RAID?

Usually, there is a RAID device created. Then we have to make a file system on that ... or partitions or LVM PV, which gets a VG and multiple LVs, then a file system is put onto each LV.

Finally, the file system gets mounted using either the mount command at the prompt for testing/temporary stuff or through the fstab or through systemd-Unit files or through a manually created script that gets called.  99% of the time, you want to use the fstab method.

As to how you "mount something on my raid disks" - I haven't a clue. The terminology isn't close enough to understand the intention.  The last sentence says " how do i mount /backup on the array" - that would properly be stated - "how to I mount the file system on my array to /backup."

There are lots of examples for fstab entries in these forums.  Or  [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
But if the array isn't "assembled" and doesn't have a file system (mkfs) already, it won't work.

---

