---
title: "DeviceDisappeared"
date: 2011-01-20
forum: Server Platforms
---

### Post by cgauss on 2011-01-20
Earlier this week I got the following message from one of my Ubuntu boxes:

Host            : Host2
MD Device       : /dev/md2
Event           : DeviceDisappeared

/proc/mdstat dump:
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sda2[1] sdb2[0]
3903680 blocks [2/2] [UU]

md0 : active raid1 sda1[1] sdb1[0]
29294400 blocks [2/2] [UU]

unused devices: <none>


md2 was a RAID array for my /home.  It looks like sda3 is still mounted for /home.  Is there anyway I can recreate this array on the fly?

---

