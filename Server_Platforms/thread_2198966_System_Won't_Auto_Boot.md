---
title: "System Won't Auto Boot"
date: 2014-01-11
forum: Server Platforms
---

### Post by unsoc on 2014-01-11
I installed a few spare drives in my system and ever since I'm having problems with the system booting it self. A few of the errors I saw are

mounting /dev/shm [696] terminated status 1 and said /dev/temp already mounted /dev/shm I looked in the fstab and not sure how it should be.

The last 2 lines are the hard drives I added as spares in /mnt/data and /mnt/data1 

Here is the fstab file

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=da67c61c-538c-47ee-8d8a-e0669e77b47c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9f9af5a6-48b2-4521-af70-c9f59364f743 none            swap    sw              0       0
tmpfs     /dev/shm     tmpfs     defaults,noexec,nosuid     0     0
UUID=01CF0EED3D95F6F0 /mnt/data ntfs users,defaults 0 0
UUID=01CF0EED9BF75770 /mnt/data2 ntfs users,defaults 0 0

---

### Post by volkswagner on 2014-01-12
I think you want to change /etc/fstab entries related to ntfs disks to look like this:



```
UUID=01CF0EED3D95F6F0 /mnt/data ntfs-3g rw,auto,user,fmask=0111,dmask=0000
UUID=01CF0EED9BF75770 /mnt/data2 ntfs-3g rw,auto,user,fmask=0111,dmask=0000
```

The above assumes you want everyone to have access and the drive should be writable.

Check out [this how to]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") if you want to modify the permissions.

---

