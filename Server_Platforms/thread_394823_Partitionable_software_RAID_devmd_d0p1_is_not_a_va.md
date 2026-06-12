---
title: "Partitionable software RAID: /dev/md_d0p1 is not a valid block device"
date: 2007-03-27
forum: Server Platforms
---

### Post by raq on 2007-03-27
Hello everybody:

I am installing Ubuntu 6.10 on an storage server of 15 * 750 GB SATA disks. I made two  RAID5 arrays of 4.5 TB each and exporting them using the 'vblade' daemon. In order to have a good performance I have had to create a partitionable raid arrays (exporting the hole array instead of one partition degrades performace 60%. I don't know why)like this:

 mdadm --create /dev/md_d0 --level=5 --raid-devices=7 --spare-devices=1 --auto=part /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdp1

And /etc/mdadm/mdadm.conf:

DEVICE /dev/sd[bcdefghijklmnop]1

ARRAY /dev/md_d0 UUID=11eadd8d:e8d59382:dfe5d988:c871b467 spare-group=jffstg01 auto=part
ARRAY /dev/md_d1 UUID=863c1be0:05b476bc:6445e7df:eac97747 spare-group=jffstg01 auto=part

PROGRAM /usr/sbin/handle-mdadm-events

Finally I used 'parted' to make a 'gpt' labeled big partition with the whole available space and using a JFS filesystem. Everything is running fine, BUT, when restarting RAID arrays:

/etc/init.d/mdadm-raid stop
/etc/init.d/mdadm-raid start

Now, I can NOT access the RAID partition again. If I try to remount it says:

mount: /dev/md_d0p1 is not a valid block device

I MUST reboot the system in order to mount/export/check the partitions again. 
Is something wrong with partitionable software RAID or I am doing something w:) rong?.

Help would be very apreciated as I want this server as stable as possible.

Thanks in advance

---

### Post by BoneKracker on 2007-04-17
I've never used partionable raid.

You can alternatively create a number of smaller raid devices and then use LVM to concat them into a large logical volume group.  That then is paritionable as logical volumes.

---

