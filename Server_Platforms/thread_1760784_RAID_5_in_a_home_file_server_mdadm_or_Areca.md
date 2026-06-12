---
title: "RAID 5 in a home file server: mdadm or Areca?"
date: 2011-05-17
forum: Server Platforms
---

### Post by Ron Jones on 2011-05-17
I've decided to build a low-cost file server for my household, which will consist of 5-6 users storing the bits of information that adults and teenagers in a typical household seem to collect (audio, video, various documents, and not enough schoolwork).

There's a spare 4U box in the rack, and I've ordered a Gigabyte [GA-M68MT-S2P]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128469") from the Egg (unique in its exclusive use of SATA ports)... Along with three (3) 500 GB Western Digtals, an Athlon II Dual Core 3.0 GHz processor, and a SATA dvd rom drive.

I'd like to configure a RAID 5 array, and was all set to order an Areca ARC-1210 card... until I read that the Linux software Raid performs admirably. 

High availability is NOT a priority. If a drive fails, I'll just shut her down, replace the drive, and start back up (an hour, or a couple of days won't matter). 

Throughput in a 5-user environment shouldn't be an issue, so I don't want to introduce the complexity of stripes or plaids.

Ease of administration IS a preference though. When I replace a bad drive, and bring the machine up, I don't want to be faced with an instruction set so confusing that I run the risk of erasing everything while trying to add the new drive to the array.

According to the instructions at [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) it looks like even I could configure it. 

HOWEVER... it appears that with a Raid 5 array, there is some extra configuration required for the /boot partition.

Can someone point me to a "Romper Room" level resource that I can follow to configure a software Raid 5 array... or suggest why a hardware controller might be in my best interest?

Thanks,

---

### Post by rubylaser on 2011-05-17
mdadm is very simple to setup and use.  Unfortunately, you cannot boot from a RAID5 array.  If you choose to use it, I'd either suggest you use a separate hard drive for the OS, or partition each of your disks, and setup a RAID1 array for the /boot and and a RAID5 array for the data (this isn't hard, but definitely isn't entry level mdadm stuff :) )  Those directions you linked to should setup this exact scenario, a RAID1 / volume, and a RAID5 data volume for all the rest of your stuff.

At home I boot of a 30GB SSD, and have my 8 1TB drives in RAID6 via mdadm.  It works very well, and I've been using mdadm for years with no problems.  If you have any questions, please feel free to post here, you'll get lots of help.  The directions at the bottom of that wiki page even demonstrate some basic management tasks.  You'll just want to install smartmontools so that you can monitor your hard drives health, and get email warnings if a disk is failing or has failed.

---

### Post by Ron Jones on 2011-05-17
Excellent. Thanks!

So basically, all I've got to do is set up a partition on each of my 3 drives (say... 250MB) and designate it as Raid 1. Then use that as /boot ... and configure the remaining space on each drive into a Raid 5 array?

Using the alternate installation image of Ubuntu server, will I need to manually configure the partitions in the remaining space?

I might even be able to handle that.

---

### Post by rubylaser on 2011-05-17
That's exactly right.  It should be fairly straightforward with those directions (I'd probably give myself a little more space (500 MB) for /boot in case you accumulate a few older kernels prior to cleaning them out).

---

### Post by SpaceBas on 2011-05-17
Ron, congrats! what a fun project. Like rubylaser suggested, its a fairly ease thing to get up and running. 

I've been doing exactly what you described for 5 or 6 years and probably didn't have your level of knowledge when I started. Some things I've learned along the way: 
* software raids are more reliable than they were a few years ago and were surprisingly reliable then. Mine has taken many lickings and kept on ticking. In fact, you may want a bash job or something similar mail you some logs on a daily or weekly basis. I had a drive remove itself, it was out of the raid for months if not a year before I realized it. Didn't affect performance, although it did affect fault tolerance.  (re-reading I see that rubylaser suggests smartmontools, good call!) 

* mdadm is deceptively powerful. Make sure to keep frequent backups of your config files off site. I've lost a few arrays in the past due to hardware or user error. Having the config file with the suid of the array is a must. 

* ditto the SSD + raid suggestion. Or frankly, just the separate boot volume + raid. I've started putting SSDs in most of my machines for boot drives. Its a nice luxury, although not one you will take much advantage of on a server.

---

### Post by spynappels on 2011-05-17
I've been doing some work on this for myself, and did a fair bit of testing in a Virtual environment.

I built myself a "RaidLab" machine just to see how I could get it to work. My machine has 3x250GB HDDs, 2x160GB HDDs and a 2GB USB Flash Drive.
I partitioned the 2GB Flash drive with 100MB ext2 partition, 1GB ext4 partition and the rest swap space. All the HDDs were partitioned as Physical RAID disks.
I then assembled the 250GB drives into a RAID5 array and the 160GB drives into a RAID1 array, and partitioned both arrays as ext4.
I did all this from the default server install disk under manual partition. I set the 100MB Flash partition as the /boot, the 1GB Flash partition as /, the 500GB RAID array partition as /home and the 160GB RAID array partition as /var.
I then installed server edition on it and it all went well. The Flash drive is the boot device, but will have much less write cycles as the /home and /var folders are on the RAID arrays.
I guess SSDs would work better, but I don't have money for them, and a Flash drive makes a good alternative for a testing or home environment.

---

### Post by rubylaser on 2011-05-17
A CF card or thumb drive will work very well too (or using a persistent live-cd on your thumb drive). Although, I wouldn't put the swap partition on your flash drive ( you may want to build a raid partition for your swap space, to prevent crashes should your flash drive fail), and I'd move /tmp into tmpfs as well.

---

