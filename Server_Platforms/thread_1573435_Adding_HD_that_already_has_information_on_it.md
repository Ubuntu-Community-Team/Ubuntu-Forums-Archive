---
title: "Adding HD that already has information on it"
date: 2010-09-12
forum: Server Platforms
---

### Post by 1serveyou on 2010-09-12
Hi everyone, I'm trying to switch over my old server(9.10) data to a different server(10.04). My old server only had 2 drive bays, whereas my new one has 4. I already have my new server up and running(for the most part), and want to add the old hard drive to it. How would I do this without losing any information. I believe even my old drive is formatted to ext4. I was going to just throw it in there, but I'm afraid of losing information as I really don't want to lose a 1tb of info. Any help would greatly be appreciated!

I did try to search, but my title had too many common words in it.

---

### Post by oldfred on 2010-09-12
I would just plug it in. If possible make sure to use a higher SATA port if SATA. If IDE/PATA it may depend on the BIOS, some seem to promote IDE drives to sda others do not. If all drives are PATA make sure jumpers are correct.

Check in BIOS right after plugging in to see how BIOS sees it.

Also, make sure you still are booting from your existing boot drive in BIOS.

---

### Post by 1serveyou on 2010-09-14
> **oldfred said:**
> I would just plug it in. If possible make sure to use a higher SATA port if SATA. If IDE/PATA it may depend on the BIOS, some seem to promote IDE drives to sda others do not. If all drives are PATA make sure jumpers are correct.
 
Check in BIOS right after plugging in to see how BIOS sees it.
 
Also, make sure you still are booting from your existing boot drive in BIOS.
 
This is going to show my noobness when it comes to drives, but once I install the physical drive, how do I access those files. I know I have to mount, but how do I mount "folders" that are already on the hard drive.
 
Also all hard drives are SATA. My end result is having the OS drive(1), Data1[1tb used in old server that I need to install](2), Data2[1tb new hard drive I have to install](3), and Backup1[2tb hard drive I need to purchase/install](4).

---

### Post by oldfred on 2010-09-14
If you have drives you permanent want to mount you need to edit fstab and understand mounting: 

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

$ sudo mkdir /Data
$ sudo mount /dev/sda5 /Data
where sda5 needs to be your drive, partition
if not known to list partitions
sudo fdisk -l

If you cannot read and write then change the permissions. Not for NTFS

$ sudo chmod -R 777 /Data
sudo chown -R fred:fred /Data
where fred should be your login name

I prefer the control manual editing gives, but
Some think it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

Some are now recommending mountmanager also in synaptic:

You can also mount a partition and then link folders into /home.

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments by Morgan Hall
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions (post #5) of data linking from above blog, based on more from comments 
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

With large drives some like to have an operating system on every  drive. I have several copies of Ubuntu and have them on different drives.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

---

### Post by 1serveyou on 2010-09-15
Thanks for the help, it said it couldn't find a partition on it(old data server hd). But when I put it back into my old server it worked fine. I put it in unused 1tb, formatted it and have that working and will transfer the files over.

---

