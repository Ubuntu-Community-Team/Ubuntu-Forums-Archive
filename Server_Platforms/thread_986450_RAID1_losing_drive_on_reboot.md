---
title: "RAID1 losing drive on reboot"
date: 2008-11-18
forum: Server Platforms
---

### Post by ilikesoup on 2008-11-18
So here is my setup, I have two 80gb disks in a RAID1, the RAID1 is /dev/md0, comprised of /dev/sdb1 and /dev/sdc1. One of my disks failed (sdc1), so I removed it from the array and replaced it with a fresh drive.

I used sfdisk -d /dev/sdb > partitions.sdb
which dumps the disk partition table format to a text file, then restored it to the new drive with:
sfdisk /dev/sdc < partitions.sdb

This works fine, and writes the partition table, so the tables are the same.

Then i use mdadm /dev/md0 --add /dev/sdc1
and it adds the drive successfully, and starts building the array. Here is a cat of /proc/mdstat while it is rebuilding the array

md0 : active raid1 sdc1[2] sdb1[0]
      73240192 blocks [2/1] [U_]
      [======>..............]  recovery = 33.5% (24560256/73240192) finish=14.3min speed=56599K/sec


After it finishes everything looks healthy, and /proc/mdstat looks good. Here is mdadm --detail /dev/md0


(I'll grab this after it fully rebuilds... again)


Here is /etc/mdadm/mdadm.conf

ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 UUID=5d02a4f3:0460e5f4:024d341c:4b9fc933
   devices=/dev/sdb1,/dev/sdc1


Ok so finally, here is the problem. After I reboot, /dev/sdc1 is gone, and the RAID is running on one disk (/dev/sdb1). /dev/sdc1 doesn't exist. If i do a fdisk -l /dev/sdc, it shows the proper partition table, but it's like it's not written to disk anymore. if I go into fdisk and press "w" it writes the partition tables to disk again. But the whole process repeats itself on the next reboot/rebuild of the array.

I've done this like 5 times, with the exact same results. Help please!

---

### Post by fjgaude on 2008-11-18
I trust you are not thinking that /sdc and /sdc1 are the same.

---

### Post by ilikesoup on 2008-11-18
> **fjgaude said:**
> I trust you are not thinking that /sdc and /sdc1 are the same.

lol, yeah, When i was typing up the post i realized how easy it was to forget the 1 or add it where it was not suppose to be. I actually did make a mistake, but I edited it in the origional post and fixed it... 

it's still weird to me that fdisk could see the partition table, but the device /dev/sdc1 didn't exist... 


I *JUST* got the RAID working... I wrote zeros to the drive with `dd`, and did all the same steps to duplicate the partition table with sfdisk, and it's surviving reboots. Now I just have to put grub on the second drive, so it can boot from both drives.

I'll call this one RESOLVED... for now.

---

### Post by fjgaude on 2008-11-19
Great, we all learn new things each day, if we keep our minds open.

---

