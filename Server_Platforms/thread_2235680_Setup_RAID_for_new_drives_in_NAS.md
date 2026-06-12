---
title: "Setup RAID for new drives in NAS"
date: 2014-07-22
forum: Server Platforms
---

### Post by simon48 on 2014-07-22
New to Linux but have just setup Ubuntu Server 14.04 on a 1TB drive and working great in my HP Microserver. Will keep this drive for OS, booting and general files only.

Now going to set up 2 x 3TB drives for media and want to set these up as RAID 1 in case one of these drives fails.

Seen I can set up RAID during initial install, but how do I firstly setup, partition and format the 3TB drives and how do I set them up as RAID 1 from a running system?

Not using a GUI at the moment so didn't know if GParted would run.

Found various suggestions but most seem to assume the OS drive is part of the RAID array and for new installs only.

Many thanks,

Simon

---

### Post by TheFu on 2014-07-23
Don't have time to research the exact answers, sorry.

You can run gparted from a thumb drive boot or liveCD.

Adding software-RAID to new HDDs (or partitions) added to the system post-install is easy (I vaguely remember).  mdadm is the tool and there are many how-to guides. google "ubuntu software raid"

Because it is my nature, I'd stress that RAID shouldn't be used unless there is already a great, working, backup solution. RAID does NOT replace backups, ever. RAID is for HA - high availability. It doesn't solve 99% of the data protection needs for most people that backups solve completely.

---

### Post by thufirhawat2 on 2014-07-24
Hey, welcome to Linux! I have traditionally set my RAIDs up at install time, but I had a recent experience (just look down a few posts on this forum) where I had to rebuild an array the old fashioned way, so here are my tips and reading materials:

1:[http://computernetworkingnotes.com/disk-managements/raid.html](http://computernetworkingnotes.com/disk-managements/raid.html)

Once you have physically installed and connected your new drives, you will have to create a partition on each one that is configured as Linux raid autodetect using the fdisk commands, which must be run as superuser. It is kind of like a text based wizard, so you would start by typing ```
sudo fdisk -l
``` to get a listing of your drives and how they are mapped. Then, ```
sudo fdisk /dev/sdb
``` assuming your first new drive is sdb. At that point, you can type m to see how you need to proceed to create a new partition using all of the space on the drive formatted as Linux raid autodetect.

2:[https://raid.wiki.kernel.org/index.php/RAID_setup#Using_the_Array](https://raid.wiki.kernel.org/index.php/RAID_setup#Using_the_Array)

If it is not already installed, you will need to install mdadm, and it is a pretty simple command to initially build the array, something like ```
mdadm --create --verbose /dev/md0 --level=mirror --raid-devices=2 /dev/sdb1 /dev/sdc1
``` assuming you wanted a RAID 1 and the new partitions you created are both partition 1 on their respective drives, which they will be by default. You can then run cat /proc/mdstat to see the resyncing progress of the drives. I recommend letting them finish resyncing before you do anything else. This can take a while, and there is no documentation supporting my recommendation as far as I know in this case, but that is what I do.

3:[http://www.linuceum.com/Server/srvRAIDAuto.php](http://www.linuceum.com/Server/srvRAIDAuto.php)

Mount the array. You will want to edit the fstab and mdadm.conf files to make sure the server will automatically remount the array on a reboot. Where you mount it is up to you; I only have one user on my NASs at work, and so I just mount the raid as /home so I can easily set up samba shares that will be stored on the array. Just make sure wherever you mount it, the permissions for that location will accommodate what you want to use the storage for.

Very brief, but that should get you going.

---

### Post by TheFu on 2014-07-24
Be careful using fdisk on GPT or drives over 2TB in size.  **parted** is the replacement command - or **gparted**.

---

