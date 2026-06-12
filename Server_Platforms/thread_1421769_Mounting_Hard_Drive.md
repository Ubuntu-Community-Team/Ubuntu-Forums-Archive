---
title: "Mounting Hard Drive"
date: 2010-03-04
forum: Server Platforms
---

### Post by rabil on 2010-03-04
I'm running Ubuntu 9.10 64-bit.

For some reason, the second hard drive (sdb1) is not automatically mounted:

rick@rab-1:/mnt$ sudo fdisk -l

Disk /dev/sda: 500.0 GB, 499989348352 bytes
255 heads, 63 sectors/track, 60786 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c17f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59332   476584258+  83  Linux
/dev/sda2           59333       60786    11679255    5  Extended
/dev/sda5           59333       60786    11679223+  82  Linux swap / Solaris

Disk /dev/sdb: 500.0 GB, 499989348352 bytes
255 heads, 63 sectors/track, 60786 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00046051

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60786   488263513+  8e  Linux LVM


If I try to mount it manually:

rick@rab-1:/mnt$ sudo mount /dev/sdb1 /mnt/sdb1
[sudo] password for rick: 
mount: unknown filesystem type 'LVM2_member'


Before I installed Ubuntu, I installed the RAID software to handle 4 500 GB hard drives - so there are supposed to be two mirrored drives. I'm not an expert in using RAID. I'm assuming it is correctly configured. I only "see" two drives. sda has Ubuntu etc. How can I get sdb1 mounted? What am I doing wrong? I've tried using the palimpsest program but I'm afraid I screw it up. Do I need to re-format sdb1?

Thanks.

---

### Post by richardjh on 2010-03-04
How was this partitioned in the first place?

Are you expecting any data to be on sdb1? It is formatted using LVM (logical volume manager) so you wouldn't mount it as you are trying to do.

If you just want to wipe the disk and get it mounted as a new drive that is easy to do and I will explain. If you think the disk should already contain your data, that changes things, as we will need to mount the logical volume contained within the volume group.

---

### Post by FiveSidedPoly on 2010-03-04
Hi!
 
I'm not experienced enough with raids or LVM in Linux, but it seems that either something is wrong with the partitioning or formating.
 
Did you configure the RAID during the install or was the raid software you used external to the install?  From the looks of it it looks like you have LVM setup as well.
 
 
This: *mount: unknown filesystem type 'LVM2_member' *makes me think that how it is setup is the issue.
 
Did you enter and or are the disks showing up properly in /etc/fstab?
 
What version of Ubuntu Server are you using?
If it's 9.10 maybe you can find something out here, I've used it before:
[https://help.ubuntu.com/9.10/serverguide/C/advanced-installation.html](https://help.ubuntu.com/9.10/serverguide/C/advanced-installation.html)
 
If that doesn't help at all, I hope someone more experienced can help  :)

---

### Post by rabilon on 2010-03-04
I just want to be careful. I don't think anything is on the sdb1 but because I can't mount it I can't check. I installed the raid software before installing Ubuntu. First I installed 9.04 and then upgraded to 9.10. As far as I can tell, the Ubuntu is on sda1. I thought when I installed Ubuntu it would have automatically set things up to mount sdb1 also, but I guess not. When I look at sdb1 using palimsest, the only option I'm given is to erase sdb1.

---

### Post by rabilon on 2010-03-04
Given it's formatted as LVM, how would I mount sdb1?

---

### Post by richardjh on 2010-03-05
You need to do (as root) a 

```
vgscan
```See if you get any volume groups found. If you do then

```
vgchange -a -y
```Will enable them as devices, depending on how the LVM was set up in the first place, will effect where these are. For me it is /dev/vg0/root /dev/vg0/var and so on but it will likely be different for you.

You will then be able to mount the devices using something like

```
mkdir /mnt/root 
mount /dev/vg0/root /mnt/root
```and then see what is on them.

I don't understand how this disk got to be as described, do you know what may have caused the disk to be LVM in the first place?

Obviously as these are commands run as root, you should look this up elsewhere first to understand a bit more about it and to decide for yourself if you want to continue with this.

---

### Post by rabilon on 2010-03-05
Thanks. I will try this when I get to the server. I had used CentOS initially but ran into too many problems, so I switched to Ubuntu. CentOS likely set up the drive but I don't remember the details.

---

