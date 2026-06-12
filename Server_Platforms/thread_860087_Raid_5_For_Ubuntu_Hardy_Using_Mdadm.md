---
title: "Raid 5 For Ubuntu Hardy Using Mdadm"
date: 2008-07-15
forum: Server Platforms
---

### Post by santhony on 2008-07-15
I thought it was important to POST my experience, as a newbie to creating a RAID ARRAY using MDADM in UBUNTU HARDY.

It's not hard at all setting up MDADM, provided you have no hardware issues and MDADM has no bugs on your platform..  MDADM will usually auto detect RAID Arrays on systems.  So little effort is required to start an array or import one into a new system..  

Here' are the steps it took me to create a Raid 5 ARRAY using MDADM.  My hardware configuration required me to have the latest MDADM, where I was experiencing allot of issue with getting my ARRAYs to reload after booting.  I updated to the unstable version mdadm_2.6.7-3.  File name was mdadm_2.6.7-3_i386.deb

Here's the URL to MDADM Updates. 

[http://packages.debian.org/sid/mdadm](http://packages.debian.org/sid/mdadm)

Keep in mind, these are all the latest versions, some are unofficialy released and unstable.. Only update here if you beleive you are experiencing issues and believe you need to update to resolve.

PREPARE DRIVES FOR RAID
Format drives with gparted, you can use ext2 or ext3 or resiers filesystems
change flags on partitions to raid.  After performing these, file type will be FD Linux raid autodetect, to confirm this, run
fdisk -l from command prompt.

Run this command to show your drives and confirm they are FD LINUX RAID AUTODETECT

sudo fdisk -l
*************************************
santhony@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bab3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect
**************************************




CREATE RAID ARRAY - 
Keep in mind, your local drive letters and numbers will or may be different.
My raid ARRAY is md0
My drive partitions sda1, sdb1, sdc1

sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1 --auto=md

- This next command will give you status as the ARRAY is created.
watch -n1 'cat /proc/mdstat' 

- You can go ahead and format the ARRAY while it is SYNCING, you don't have to wait the few hours it will take to complete
mke2fs -j /dev/md0

- Make a directory to mount this drive into, I used /mnt/raid.
mkdir /mnt/raid
mount /dev/md0 /mnt/raid


These are commands you can use to provide status or detailed information about your array

cat /proc/mdstat  
mdadm -D /dev/md0
sudo mdadm --detail --scan --verbose


UPDATE SYSTEM FILES TO AUTOMATICALLY LOAD RAID
-System File to Load Raid ARRAY

 mdadm --detail --scan --verbose
*********************************************
santhony@ubuntu:~$ sudo mdadm --detail --scan --verbose
mdadm: metadata format 00.90 unknown, ignored.
ARRAY /dev/md0 level=raid5 num-devices=4 metadata=00.90 UUID=67350c39:89f0ac91:0f5b4e61:2c17f314
   devices=/dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1
*********************************************
This output is placed into the mdadm.cfg file.  YOu should see a previous entry in this file, the default configuration...  If you get it wrong, it shouldn't blow up your array or cause any irreverisble damage.  This just helps the array to auto build during the boot process.

-Edit the mdadm.cfg with the new array info from the command mentioned above.
/etc/mdadm/mdadm.cfg

-This file is so the system will auto mount the new array at boot.  Again, if you get this wrong, no irreversible damage..  It just won't auto mount and you will have to manually mount it after booting.

-System File to Mount Raid Array
/etc/fstab

Here's how mine looks:

/dev/md0 	/mnt/raid	auto	defaults	0 0


This should be it.  



EXTRA INFO: 
GROW RAID
mdadm --add /dev/md1 /dev/sdf1
mdadm --grow /dev/md1 --raid-devices=4

umount /dev/md0
sudo e2fsck -f -v /dev/md0

sudo resize2fs -p /dev/md0


RECREATE ARRAY
sudo mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
sudo mdadm --assemble --scan


REMOVE RAID ARRAY

sudo mdadm --stop /dev/md0
sudo mdadm --remove /dev/md0


UPDATE MDADM
[http://packages.debian.org/unstable/admin/mdadm](http://packages.debian.org/unstable/admin/mdadm)

LINKS TO SOME OTHER TUTORIALS:

[http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188) (GOOD EXPLANATION OF HOW TO)

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Edit_The_.2Fetc.2Ffstab_File](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Edit_The_.2Fetc.2Ffstab_File)

[http://scotgate.org/?p=107](http://scotgate.org/?p=107)

ANYONE ELSE - PLEASE ADD TO THIS FORUM, AS I HAVEN'T SEEM MUCH ON MDADM IN UBUNTU HARDY.

---

### Post by jdavis on 2008-07-15
Excellent post! I have been using RAID1 on one of my systems for a few years and I do remember struggling setting things up due to lack of info/guides available. What I want to ask is do you have any experience of monitoring the arrays using mdadm?

I know some sections of the config file relate to notification of errors in the array, although I remember struggling with it in the past (probably around 6.10 ish) and haven't had another go since then.

Jonathan

---

### Post by fjgaude on 2008-07-15
Thanks for the detailed instructions for using **mdadm**.

Question: What was it about your hardware that caused you to upgrade mdadm to version 2.6.7?

I use 2.6.3 without issues. I've used whatever came with the Ubuntu release for the last two or three years without any problems, from AMD to Intel CPUs and different motherboards.

Curious to what the changes are and how they improve the program overall.

---

### Post by gaspedalo on 2008-07-15
Well done, very straight forward! Thanks for that guide.
Do you think that there is a way to implement a raid5 array as boot device?

---

### Post by tomaslo on 2008-09-05
Thans for this excellent guide!

I installed mdadm using aptitude on 8.04.1 and everything is working fine.

---

### Post by fjgaude on 2008-09-05
I know of no way to boot from a software raid5 array... most who have tried have failed.

---

