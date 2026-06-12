---
title: "/proc/mdstat showing sda instead of sda1"
date: 2010-03-10
forum: Server Platforms
---

### Post by kw1111 on 2010-03-10
I have a RAID 1 array managed by mdadm that has recently had a drive fail.  I'm having trouble with knowing what to do at this point.  Normally I would just run:

mdadm --add /dev/md1 /dev/sdb1

since sdb is the device that failed.  However, when I look at the /proc/mdstat it is telling me that the remaining device is /dev/sda instead of /dev/sda1:

cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sda[0]
      488386496 blocks [2/1] [U_]

md0 : active raid1 sdc1[0] sdd1[1]
      77047616 blocks [2/2] [UU]

Can anyone help me understand why sda is showing instead of sda1?  Once that is resolved I would also like some help getting the new drive added, which is larger than the original drive.

---

### Post by joeinbend on 2011-01-24
Really old post here, but I thought I'd answer your question anyway: All that means is that your disk was used as a member of your RAID array without any partitioning being done. I do this personally as well for my RAID, however may people will argue (rightfully so...) that you should actually partition your disks down by a few MB. The reason for this is, if you go and replace a disk later and it is a different manufacturer and happens to be just a few bytes smaller than your other disks, you cannot add it, because it has to be at least as big as the other drives.

So, in your case, that /dev/sda is the full disk, and you will want to look at the size of your other RAID members (sudo cat /proc/partitions), if they are all partitioned (meaning they are /dev/sdx1 instead of /dev/sdx) then you will want to partition your disk with fdisk to exactly the same size as the other RAID members, this is sort of a "best practices" thing to follow to keep from painting yourself into a corner later (as I arguably have done... but for my own reasons am not concerned about it).

---

