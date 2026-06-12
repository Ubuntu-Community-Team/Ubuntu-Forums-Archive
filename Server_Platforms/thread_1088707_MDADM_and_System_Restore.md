---
title: "MDADM and System Restore"
date: 2009-03-06
forum: Server Platforms
---

### Post by Setsuna666 on 2009-03-06
Hi, 

We currently have the following setup for our file server in raid0 using MDADM and I am trying to make an how to for our company in order to be able to restore the system in case of crash.

Here is the setup:

/dev/sda1 - 100MB - Boot - The Boot partition outside the raid array
/dev/sda2 - 100GB - RAID 
/dev/sda3 - 700GB - Extended
/dev/sda5 - 655GB - RAID 
/dev/sda6 - 5GB   - RAID 

/dev/sdb1 - 100MB - Not used
/dev/sdb2 - 100GB - RAID 
/dev/sdb3 - 700GB - Extended
/dev/sdb5 - 655GB - RAID 
/dev/sdb6 - 5GB   - RAID

MDADM Arrays:
/dev/md0 - System - Devices: /dev/sda2 /dev/sdb2
/dev/md1 - Data   - Devices: /dev/sda5 /dev/sdb5
/dev/md2 - SWAP   - Devices: /dev/sda6 /dev/sdb6

I am using FSArchiver to backup partition /dev/sda1, /dev/md0 and /dev/md1. I can successfuly restore the partition table, grub and the data.

My problem is the following, when everything is restored and I tried to boot the server Grub is going into initramfs and I have a message saying that /dev/md0 does not exist.

I am wondering does mdadm use UUID of the partition /dev/md0 in order to find/mount it ? If that's the case, what do I have to do in order to make everything work ?

Thanks,
Setsuna666


Solution: I had to boot from the Ubuntu 8.10 live cd, chroot into my server / system and type dkpg-reconfigure mdadm or apt-get remove mdadm && apt-get install mdadm in order to update the kernel.

---

