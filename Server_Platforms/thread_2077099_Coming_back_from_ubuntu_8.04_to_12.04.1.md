---
title: "Coming back from ubuntu 8.04 to 12.04.1"
date: 2012-10-27
forum: Server Platforms
---

### Post by rgotten on 2012-10-27
On 2008 i installed ubuntu and then i place this question on ubuntu: [http://ubuntuforums.org/showthread.php?t=788493](http://ubuntuforums.org/showthread.php?t=788493) after having the server working for 4 years, last week, i had one hard drive failing (which i had during the 4 years and replace with no problem) but when i try to replace it i have a power outrage and it screw up my complete server. So now i am about to reinstall and even though have being 4 years, i still consider myself very new and would like some advise...So this are my questions:
since I have to do everything again I would like to know what has change and I have to do it the same way or differently.

1)I had install ubuntu server 8.04, it was raid 1 (100mb) for /boot, raid 1 (2gb) for swap, Raid 5 (10gb) for / (system) and raid 5 (980 gb) for /home. this was done using 3 500 GB hard drive. My question here is if should i do the sama or do something different; ie: ext4 instead of ext3. LVM on top of the raids, or anyhting different that you will be suggest


rgotten

---

### Post by LHammonds on 2012-10-29
Do you have a backup of the partitions that you can restore?  If so, stick with 8 and restore to 8 from 8.

But if you have to re-build from scratch, might as well get the latest and make it work.

All my Ubuntu servers are configured using LVM for everything except /boot.  I have my server configuration documented step-by-step in my signature.  They are also running inside virtual machines on top of VMware vSphere 4.1.  The storage unit is a fiber-connected storage shelf with a bunch of drives configured in either RAID 5 or RAID 10.  Any failed drives is handled at the storage level.  VMware and the VM operating systems never see the true hardware or know about any problems.

I am also a stickler for multiple backups and having multiple ways of restoring or re-building a server so I use methods that backup at the partition level (FSArchiver), another at the data level (rsync) and also have detailed documentation on how each server is built and configured.  If somebody from the outside had to rebuild one of my servers (without any partition/data backups), they would still be able to bring the server back online...however, my backups have backups so there is little chance the data will disappear...unless we have a solar flare that takes out the entire state. :)

LHammonds

---

### Post by rgotten on 2012-10-31
> **LHammonds said:**
> Do you have a backup of the partitions that you can restore?  If so, stick with 8 and restore to 8 from 8.

But if you have to re-build from scratch, might as well get the latest and make it work.

All my Ubuntu servers are configured using LVM for everything except /boot.  I have my server configuration documented step-by-step in my signature.  They are also running inside virtual machines on top of VMware vSphere 4.1.  The storage unit is a fiber-connected storage shelf with a bunch of drives configured in either RAID 5 or RAID 10.  Any failed drives is handled at the storage level.  VMware and the VM operating systems never see the true hardware or know about any problems.

I am also a stickler for multiple backups and having multiple ways of restoring or re-building a server so I use methods that backup at the partition level (FSArchiver), another at the data level (rsync) and also have detailed documentation on how each server is built and configured.  If somebody from the outside had to rebuild one of my servers (without any partition/data backups), they would still be able to bring the server back online...however, my backups have backups so there is little chance the data will disappear...unless we have a solar flare that takes out the entire state. :)

LHammonds
Thanks for the information, i have taking a look into your signature and is amazing the step by step that you have provided, thanks. I do would like to ask you a few questions if you don't mind:

a) Even though backups are very important and i agree with them (they are needed), one of the thinks i liked from my software raid was that if one disk failed, just replace hard drive and rebuild with 0 down time...i have seen some places that they do raid and LVM on top...would you recommend that or not? if not why, if yes ..how will you do it...

2)I am not very familiar with the virtual machines or virtual machines on top of VMware vSphere, con you briefly summarize what is it and what will be my benefit

Your help is greatly appreciated..Thanks

---

