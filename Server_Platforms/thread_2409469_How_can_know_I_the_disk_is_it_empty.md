---
title: "How can know I the disk is it empty?"
date: 2019-01-02
forum: Server Platforms
---

### Post by sed_faster on 2019-01-02
Hello,

I have a hard disk stopped in my desk and I putted them in ubuntu server 16.04.05LTS and I get this through fdisk command:
```

Disk /dev/sdc: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 9DEC32AC-D2B1-4B9B-86XX-67C2262FGFA7

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.5 LTS
Release:    16.04
Codename:    xenial
$ uname -a
Linux ubuntunet 4.4.0-141-generic #167-Ubuntu SMP Wed Dec 5 10:38:08 UTC 2018 i686 i686 i686 GNU/Linux

```

Can I assume this disk it is empty? 

Thanks

---

### Post by oldrocker99 on 2019-01-02
There is a program called baobab, which shows directories on a disk. It'll show a circular graph, with the total bytes used in the center. Try this:
```
sudo apt install baobab
```

I hope this helps.

---

### Post by sed_faster on 2019-01-02
Can I do this with fdisk!? This is native in this system, right!?

Thanks
[B]
[UPDATE1][/B]
Remember, I am in ubuntu **Server (headless)**

---

### Post by howefield on 2019-01-02
Thread moved to the "*Server Platforms*" forum.

---

### Post by westie457 on 2019-01-02
```
sudo fdisk -l
# or
sudo parted -l
```will list any partitions on the hard drive.
```
df -h
``` will list the amount of used space on any mounted partitions.

---

### Post by sed_faster on 2019-01-02
I used fdisk to create a empy partitions and after I used mkfs.ext4 to format the partition. But when I configure my fstab and reboot the system appear during the script boot this message: [https://snag.gy/5b0aDj.jpg](https://snag.gy/5b0aDj.jpg)
This is annoying and so stupid :( Now I am trying access the system through usb image lubuntu to edit file fstab and can boot all system....

If I choose Ctrl+D the system freeze in this message! Why!?

Thanks

---

### Post by TheFu on 2019-01-08
Some people use disks directly, without partitions. This happens mostly by people doing RAID setups.  I consider NOT having a partition table in the RAID set an anti-pattern for the reason you've run into.  There might be a RAID flag set, or not. 

You can assume anything you like and live with the repercussions.

I would probably run some sort of data recovery against the disk looking for partitions and files for about 24 hrs first. [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

But the history of the drive would determine how hard I looked, if at all.  Inside a business, I'd probably put the disk on a shelf for 60 days and see if anyone notices the data isn't available somewhere. If nobody says anything, I'd wipe it and never look back.  The SMART data would tell me if using it for primary or backup storage is better.  Zero relocated sectors and  a few other parms in SMART.
At home, I might hold out longer.  I have 1 disk from 2004-ish sitting on a shelf for data recovery.  I need to find that disk. Hummm.

---

