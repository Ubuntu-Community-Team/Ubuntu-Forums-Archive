---
title: "[SOLVED] Partition Expansion Problem"
date: 2007-12-28
forum: Server Platforms
---

### Post by sportster3 on 2007-12-28
We currently have a 2TB array with 7GB for the / , 2 GB for swap, and the rest for data (backuppc).

The data partition filled up so we ordered more drives, expanded the array to ~3.3TB and then realized that we could not expand the data partition because we have an MBR partition table and MBR/fdisk doesn't support anything over 2TB.  So we got this array with a ~ 2 TB partition in the middle of it and ~1.3TB we can't use.

Anyone have any ideas how we can use this extra space.  LVM is not used.  Our raid controller is a 3ware 9500S-12.  I don't think that it will allow shrinking the array and removing drives.  There's an option for 2TB autocarving but I don't know if we can turn that on after the array is created and still keep my data.

The only option we have come up with so far is to create a 2TB+ array on another server we have (using GPT!) and copy the data.  This creates a large window when the server is down that we would like to avoid if possible.

Any ideas would be appreciated

---

### Post by insane_alien on 2007-12-30
have you tried other softare to resize the partition? maybe a gparted liveCD? 

i think it would be wise to bite the bullet and switch over to an lvm2 setup as those are very easy to manage and could make further expansion go a lot smoother with the only downtime required to be the time taken to install the new disks.

---

### Post by sportster3 on 2008-01-15
I used a gparted live CD to change the drive from MBR to GPT and created a partition starting at the same sector that my data partition started at before.  I then resized the file system take up the rest of the partition.  After I created the partition I could mount it just fine and see the data, but everytime I reboot I get an error "mount: operation not supported" when I try to mount it.  The only way I have found to get it to mount again is to recreate the partition.  I've searched google for an answer but everything seems to be talking about NTFS or ACL support...I'm not using either.

Any ideas on how get the drive to mount without having to recreate the partition after every reboot?

A little relevant info:
Ubuntu Server 7.10
the partition /dev/sda3 is reiserfs

---

### Post by sportster3 on 2008-02-21
I eventually just installed the 64bit version of 7.10 Server and didn't have this problem anymore

---

