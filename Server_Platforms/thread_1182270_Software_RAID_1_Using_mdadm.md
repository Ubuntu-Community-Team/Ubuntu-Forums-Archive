---
title: "Software RAID 1 Using mdadm"
date: 2009-06-08
forum: Server Platforms
---

### Post by smc18 on 2009-06-08
Hello everyone,

I beginning to put a small home project together and currently researching the setup.

Right now, my plans for this new server is a small home Samba File server, with the hard drives in a mirrored array.

Well I think I've decided to choose a software RAID, because I began to look at 3ware RAID controllers, and I'm not willing to spend that kind of money on a hardware RAID for a home experiment. =\

Well I've found alot of documentation on mdadm; but it seems like you have to have the OS installed first then you setup a RAID on two other drives.

My question is: Is there a way I can just use two hard drives that will include the OS in the raid array?

Thanks :)

Basic Hardware Setup:
2.8 GHz Pentium 4 - socket 478
1 GB RAM
ATi Radeon 7000 AGP card
Albatron PX865PE Lite Motherboard (Only SATA version 1)
Two 1 TB Western Digital Caviar Green WD10EADS - 32MB cache, 7200 RPM

Installing Ubuntu Server 8.04 (32bit)

---

### Post by zharmad on 2009-06-08
You could check out [https://help.ubuntu.com/community/Installation/SoftwareRAID?action=fullsearch&context=180&value=Convert+to+software+raid&titlesearch=Titles](https://help.ubuntu.com/community/Installation/SoftwareRAID?action=fullsearch&context=180&value=Convert+to+software+raid&titlesearch=Titles). Most ways I've seen involve installing the OS, setting up the raid array, then migrating the OS over onto it.

---

### Post by smc18 on 2009-06-08
*Thumbs up* for searching the documention. :)

It looks good, I'll post back if I come across any problems.

Thanks!!

---

### Post by smc18 on 2009-06-08
> Partitioning the disk
For a 2 hard drive system in RAID 1 configuration. (repeat steps for additional hard drives) 

Warning: the /boot filesystem cannot use any softRAID level other than 1 with the stock Ubuntu bootloader. If you want to use some other RAID level for most things, you'll need to create separate partitions and make a RAID1 device for /boot. 

Warning: this will remove all data on hard drives. See DrivesAndPartitions for more information. 

Select "Manual" as your partition method. 
Select your 1st hard drive, and agree to "Create a new empty partition table on this device ?" 
Repeat step 2 with your 2nd hard drive. 
Select the "FREE SPACE" on the 1st drive then select "Create a new partition" 
Select the size (suggestion, normally you want a root partition major part of the hard drive and swap which is 1.5 times the amount of ram ) 
Select Primary, then Beginning. 
Select the "Use as:" by default this is "Ext3 journalling file system" we want to change that to "physical volume for RAID" 
Select if the partition is the main "/" partition select "bootable flag" and set it to "on" 
Select "Done setting up the partition" 
Repeat steps 4 to 10 for the 2nd hard drive and the other partitions. 



Ok I have two 1 TB drives.  I just want one hard drive mirrored on the other.

When I try to partition each hard drive the same. I choose:

> use as: physical volume for RAID
bootable flag: on

And continue, it tells me 

> No root file system defined

I understand, normally, I would need a '/' and '/swap' partition but if I create the partitions for those two using ext3, making '/' bootable.  And then when I make '/' bootable, I cannot make the RAID partition bootable... which the guide says to do.

How can I include everything in the raid?

---

### Post by smc18 on 2009-06-08
Well, now that I think about it, I don't think having the swap area being in the array is a good idea.  I'm thinking it will add too much overhead with writing it to both drives at all times.

The same goes for the '/'  I pretty much only wanted the data being stored to be in the RAID...

Now my new question is.  In the guide it says to make the parition used for the mirror as "physical volume for RAID" and to make it bootable.  Well if I make that partition bootable... I can't make the '/' bootable.

And now if I have a '/', '/data', and swap area partition, on one HDD. Obviously I want the '/data' partition on the second HDD for the array.  Well what about the empty space on the 2nd HDD that isn't going to be mirrored from HDD 1; like the '/' and swap area?

Do I still need to create the exact same partitions on both hard drives? Even if I'm just setting up mirror for the /data partitions?

Forgive me if my reasoning/thinking is way off, just trying to experiment and learn. :)

---

### Post by andyrowe on 2009-06-09
> **smc18 said:**
> Do I still need to create the exact same partitions on both hard drives? Even if I'm just setting up mirror for the /data partitions?
  No, I don't think so. (but I'm still new to this) The partition on each drive for the data however will have to be the exact same size. This will leave some unused space on the one drive.

---

### Post by G-Ray on 2009-06-09
I have a setup similar to what you are looking to do. I use it mainly for backing up my files and  for home use,with nfs and rsync. I also installed apache and a couple of web apps so I can admin and access the server easier with another computer.
I have 3-raid 1 partitions [all the same size]:
7     G root
2     G swap
900  G home
With a seperate 350 Meg. boot partition on another disk.

The server package I'm using is 8.04-2 x64. I set them up during the installation using the configure raid option to setup the file system on each partition. I have not noticed any performance issues having the root file system and the swap partition on a raid devices once mdadm finished cleaning and syncing the partitions after install; though I am not using samba and since it is for home use it doesn't have alot of people acccessing it at once. You may want to consider putting more ram in your system as my research shows reading and writing from  disk is a big performance hit.

To test my system I installed several music cds on my desktop and transferred them over using nfs while accessing the system with my laptop. The transfer did slow the access down, but I attributed this to only having one network interface on the server not the raid partitions, since once the transfer ended the access time returned to normal. If there was a raid syncing performance hit I didn't notice it, though again this is a home server.

The main reason I did this setup was with my luck the disk that would go bad would be the one with the root partition on it and I would have a good disk with my data on it, but unable to access it till I installed and configured a new drive. I also made a rescue cd with the info on my boot partition incase that partition failed as well.

---

### Post by smc18 on 2009-06-09
Thanks guys,  I will continue to set up as planned:

Drive One                                    
#2 Primary '/' parition - 40GB  ext3 (Boot Flag)     
#3 Primary '/data' - 458.7 GB   raid         
#5 Logical Swap Area - 1.5GB    swap


Drive Two
#2 Primary '/misc' parition - 40GB  ext3   
#3 Primary '/data' - 458.7 GB       raid
#5 Logical Swap Area - 1.5GB        swap

No real purpose in the '/misc' partition; I'm setting it up only because it will be unused space.

BTW, I have 1 GB of RAM in the computer.  (Hopefully that will be sufficent)

Any objections to the setup?

---

### Post by sloggerkhan on 2009-06-09
No objections, though I think if you wanted to have more space in the RAID, what you do is create a small /boot partition that lives outside of RAID, and then put everything else in RAID (or LVM).

---

### Post by smc18 on 2009-06-09
So I can subtract like 500MB from the '/misc' partition, then make a '/boot' on the second hard drive?

Will this turn out nicely?

EDIT: I tried creating a 500MB '/boot' partition on the second hard drive, and I gave me some errors.  I'm going to try to use my initial setup and see how the results turn out now.

I'll keep ya posted :)

---

### Post by smc18 on 2009-06-09
New Problem: I was trying to configure my software RAID, well I realized I missed a few things, and now I want to start over.

When I try to create a new the RAID1 It says I have to delete the old RAID1

Well when I try to delete the old RAID1'md0_raid1' it says it is in use. 
 I think I have read somewhere you have to zero out a certain part of the hard drive in order to start-over.

Anyone have any suggestions?


EDIT:
I've found 

mdadm --zero-superblock /dev/sdX

But I honestly do not know what to do.  I'm still just in the intital server installation.  I cannot get to a command line unless I stick the drives in another computer.

---

### Post by smc18 on 2009-06-09
I have found this: 
> How to remove an MDADM Raid Array

1. Find out your arrays (md0, md1, etc..) using 
Code:
 sudo fdisk -l2. Query your arrays to find out what disks are contained using 
Code:
sudo mdadm --detail /dev/md0
 (or md1 or whatever)3. Shut down the array using 
Code:
sudo mdadm --stop /dev/md04. And here's the magic key ...... zero the superblock FOR EACH drive 
Code:
sudo mdadm --zero-superblock /dev/sda (or hda)
sudo mdadm --zero-superblock /dev/sdX...

Thanks to slackwarejosh.

1)What is the best way to run these commands?
  a)Boot up with the 8.04 alternate CD, and try there? If possible.
  b)Go ahead and install server on a third hard drive.  Then run the commands while the RAID drives are unmounted?

Any suggestions?

---

