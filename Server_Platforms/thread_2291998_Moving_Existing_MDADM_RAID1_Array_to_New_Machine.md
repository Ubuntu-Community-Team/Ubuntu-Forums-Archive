---
title: "Moving Existing MDADM RAID1 Array to New Machine"
date: 2015-08-24
forum: Server Platforms
---

### Post by thufirhawat2 on 2015-08-24
I have an Ubuntu 14.04.3 server that crashed this past weekend due to a failed motherboard. I have 2 X 2TB drives in the machine, and two MDADM RAID1 arrays (1 for SWAP space, 1 for / and everything else). I have a backup server that is hardware-wise identical in every way to the live machine, so I removed the hard drives from the dead machine and installed them into the backup equipment in the same SATA ports as they were in on the crashed machine. Everything booted up and seems to be operating just as before as though nothing happened. The array seems to be functioning fine, and the /proc/mdstat file currently outputs: ```

 
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sda2[0] sdb2[1]
      1950453568 blocks super 1.2 [2/2] [UU]
      
md128 : active raid1 sda1[0] sdb1[1]
      2926528 blocks super 1.2 [2/2] [UU]

```

In short, I am not currently having any issues with the move, but I remember when I originally set this server up a couple of years ago and was experimenting with MDADM arrays, it seems like moving an array to a new machine causes the UUIDs to get screwy, and future GRUB and MDADM updates would either fail or have issues on the machine indefinitely. I have a virtual server that is identical in every configuration aspect (except the hard drive sizes) that I run on this server for testing purposes using virtualbox, and from having exported/imported it in the past, it also has this issue with MDADM and GRUB updates, but I have always managed to get through them albeit with strange errors that I have never quite been able to figure out. I would like to avoid this problem on my live server if possible however. Does anyone have any advice on making certain that my array is in shape and will continue to function normally through future changes/updates? I have tried researching it, but I seem to keep getting cycled back to articles having to do with creating a new MDADM array on an existing installation which does not really pertain to what I am trying to do. Thank you for your time.

---

### Post by TheFu on 2015-08-24
I've moved an external mdadm arrays 3 times over the years - no issues with the move any of those times.
Actually, haven't had any issues besides a failed disk in about 5 yrs. That happened over a year after the last move.

---

### Post by darkod on 2015-08-29
You shouldn't have any issues. As you noticed, simply moving the disks worked. That's one of the benefits of mdadm raid.

No UUID should get screwy simply by moving a disk. In general, the UUID will only change when you reformat the partition. Even in this case, you can specify the UUID if you need the partition to have a specific one due to compatibility, configuration, etc. It doesn't always need to be random. For example, you do:
```
sudo mkfs.ext4 -U <uuid> /dev/sda1
```

That will format sda1 with the UUID you tell it to.

Grub shouldn't be affected too. The grub part on the MBR of the disk is "pointing" to parts on the same disk, for the rest of the grub files. So, since your disks are good and functioning, grub has all that it needs to work properly.

---

