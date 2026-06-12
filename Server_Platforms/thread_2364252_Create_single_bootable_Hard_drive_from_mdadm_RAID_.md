---
title: "Create single bootable Hard drive from mdadm RAID volumes"
date: 2017-06-20
forum: Server Platforms
---

### Post by BLWedge09 on 2017-06-20
I'm currently running Ubuntu 16.04 LTS with the following software RAID devices set up.

mdstat:
```
$cat /proc/mdstat
Personalities : [raid10] [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] 
md1 : active raid10 sda2[2] sdb2[5] sdc2[6](S) sdd2[4] sde2[3]
      5854208 blocks super 1.2 512K chunks 2 near-copies [4/4] [UUUU]
      
md2 : active raid10 sda3[2] sdd3[4] sdc3[6](S) sdb3[5] sde3[3]
      3891141632 blocks super 1.2 512K chunks 2 near-copies [4/4] [UUUU]
      
md0 : active raid1 sda1[2] sdc1[6](S) sdd1[4] sde1[3] sdb1[5]
      4877248 blocks super 1.2 [4/4] [UUUU]
```

md0 os my boot partition, md2 is my root partition (/), and md1 is swap.  I really don't remember why I set it up this way, but I did it back on 12.04 believe.  

Partitions:
```
udev            7.9G     0  7.9G   0% /dev
tmpfs           1.6G  155M  1.5G  10% /run
/dev/md2        3.6T  2.3T  1.2T  68% /
tmpfs           7.9G  3.5G  4.5G  44% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sdf1       2.7T  1.1T  1.6T  40% /Zoneminder
/dev/sdg1       917G  357G  514G  41% /Kimberly
/dev/md0        4.5G  108M  4.2G   3% /boot
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           1.6G     0  1.6G   0% /run/user/1000
/dev/sdh1       3.6T  2.3T  1.3T  64% /SERVER_BKUP
```

fstab:
```
$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/md2 during installation
UUID=7a270404-2d2e-47a7-88ea-cc670ea3a678 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/md0 during installation
UUID=05d8420f-d976-4782-96aa-5f7a0e4f9628 /boot           ext4    defaults        0       2
# swap was on /dev/md1 during installation
UUID=19739584-359b-43c2-bd8b-018bc632886d none            swap    sw              0       0
#Kimberly drive
UUID=b02220f9-295c-4111-83c9-9bb2d20310ac /Kimberly               ext4    relatime        0 0
#Zoneminder Drive
UUID=e47ea1df-c007-4b99-ad06-962dd834cca2 /Zoneminder		  ext4    relatime        0 0
/Zoneminder/zoneminder/images /var/cache/zoneminder/images none defaults,bind  0 2
/Zoneminder/zoneminder/events /var/cache/zoneminder/events none defaults,bind 0 2
UUID=bcdf063d-be57-4cf2-a659-0a2003f09a9c /SERVER_BKUP		ext4	defaults	1 2
```

Other than the raid devices, you can ignore most of the rest of that. So that I can repurpose the 5 2TB drives I have currently running these 3 RAIDS, I'd like to create a single bootable drive that is essentially a clone (OS and data) of the three RAIDS, so that I can boot from it and repurposed the current physical disks running the RAID.  I have a single drive that is of sufficient size to contain this (it isn't currently in the machine or mounted, but I have space for it). I can't seem to find any sort of guide or steps to go this direction.  I realize I'll probably need to boot from an ubuntu livecd or something similar to perform this.  This server does have both a CD drive and a free usb port to boot from.  It is also a 2U, so I can mount the new boot drive.  I just need some help in formatting/partitioning the drive and moving all the relevant parts over....plus figuring out how to handle GRUB.  I believe it is currently installed on the boot partition of each device in md0.  Any help or guidance would be greatly appreciated.

---

### Post by darkod on 2017-06-21
Let me see if I understand this right. From RAID you want to go to single disk OS (no raid)? Right?

---

### Post by BLWedge09 on 2017-06-21
Correct. Temporarily of course, but yes. I want to take my whole system that consists of 3 RAIDs and put it on one bootable disk.

---

### Post by darkod on 2017-06-21
In such case yes, install the new disk, boot the server with Ubuntu Desktop CD in live mode, mount the new disk and the raid arrays at temporary mount points in the live session (for example /mnt/md0, /mnt/md2), and then use rsync or cp to copy data to the partitions on the new disk.

Be careful of two important points:
1. When formatting the partitions on the new disk use the same UUID that you have currently on md0 and md2 (swap is not relevant).
2. When copying with rsync or cp make sure you keep ownership and permissions the same as currently.

---

### Post by BLWedge09 on 2017-06-21
Ok, I'm assuming you are saying to use the same UUID for each partition to avoid having to change fstab. 

How do I handle GRUB? It's currently installed on each disk of the array... I plan on physically removing those disks and running totally off the new disk.

---

### Post by darkod on 2017-06-21
Yes, the same UUID from current arrays to the corresponding partition that will replace them.

For grub it could be little tricky, you should be able to install it from live mode knowing which is your new root partition.

---

### Post by BLWedge09 on 2017-06-24
Thanks. Everything worked as it should for the most part. Grub2 tried to be a pain but I ended up adding the necessary ppa and pulling in the boot-repair package and it worked like a charm. Thanks for the help.

---

