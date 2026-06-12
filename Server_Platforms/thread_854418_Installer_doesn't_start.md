---
title: "Installer doesn't start"
date: 2008-07-09
forum: Server Platforms
---

### Post by DualFusion on 2008-07-09
Hi,

I am using a desktop for a simple home server solution. It used to have a Windows OS, but I replaced it with Ubuntu sometime later so I could make it with Ubuntu. I used it for about a month then ceased. Now, two months after I stopped using the computer I want to give it life again so I upgraded the RAM and changed the HDD and some other things, and the installer won't boot anymore.

I've tried the live cd, live dvd, alternate dvd, everything for my architecture (x86) and it still won't work. When I start the computer, a HP home screen appears with options, then soon later, my DVD-ROM drive begins to whirl, so I know its trying to read the disk, but all that appears is a black screen with flickering "_" (underscore) character. Same happens if there is no disk. And I made sure I didnt just burn the ISO file onto the disks like regular files, I burned the images and that it boots to the CD/DVD drive first. Help?

EDIT - Some Specs:
CPU = Intel Pentium III processor 1000 MHz
RAM = 256 MB + 512 MB

Thanks,
Kevin.

---

### Post by pytheas22 on 2008-07-09
First of all, are you sure that the RAM that you added is compatible?  Since your computer's specifications are low, I imagine that your motherboard is on the old side, so make sure that the RAM you're using is the right type (e.g. SDRAM, DDR, DDR-2) and runs at a speed supported by the motherboard.  It's also possible that the RAM you bought is bad.  Maybe you could try removing the new RAM stick to see if the computer boots then.

Also, have you tried booting to any other disks (like a Windows install CD) in order to track down whether the problem is Ubuntu or a broader issue with your machine?

---

### Post by DualFusion on 2008-07-10
Hi I am trying to install Ubuntu 8.04 server on a desktop of mine and on the section where I choose which packages to select, I chose OpenSSH and when the installer begins, I get an error:

> Select and install software
Installation step failed
An installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is: Select and install software

I then choose to save the logs and in it towards the end, I get this:

> Jul 11 00:29:45 in-target: Failed to fetch cdrom:[Ubuntu-Server 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/pool/main/f/fuse/libfuse2_2.7.2-1ubuntu2_i386.deb  Hash Sum mismatch
Jul 11 00:29:45 in-target: 0 upgraded, 91 newly installed, 0 to remove and 0 not upgraded.
Jul 11 00:29:45 in-target: Need to get 0B/24.7MB of archives.
Jul 11 00:29:45 in-target: After this operation, 84.9MB of additional disk space will be used.
Jul 11 00:29:45 in-target: E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
Jul 11 00:29:45 in-target: tasksel: aptitude failed (100)
Jul 11 00:29:46 main-menu[3369]: WARNING **: Configuring 'pkgsel' failed with error code 1 
Jul 11 00:29:46 main-menu[3369]: WARNING **: Menu item 'pkgsel' failed. 

I have 2 HDD's in there and I have tried using other HDD's in case one of them was corrupt (but for some reason the base system installed correctly, so I wasn't sure). Help?

Thanks,
Kevin.

---

### Post by overdrank on 2008-07-10
> **DualFusion said:**
> Hi I am trying to install Ubuntu 8.04 server on a desktop of mine and on the section where I choose which packages to select, I chose OpenSSH and when the installer begins, I get an error:



I then choose to save the logs and in it towards the end, I get this:



I have 2 HDD's in there and I have tried using other HDD's in case one of them was corrupt (but for some reason the base system installed correctly, so I wasn't sure). Help?

Thanks,
Kevin.

Hi and welcome, have you tried what was recommended in your other thread
[http://ubuntuforums.org/showthread.php?p=5352005#post5352005](http://ubuntuforums.org/showthread.php?p=5352005#post5352005)
Also I have to ask but have you checked the cd for errors and also the checksum on the iso if you burned the cd
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by DualFusion on 2008-07-10
Hmm, well i found out it only happens when there is a second drive. I have tried 2 different HDD's and it wont work, when ever i only tried it with one HDD it worked perfectly. I will try another IDE cable and get back with you.

---

### Post by Sef on 2008-07-10
Merged threads and moved to Server Discussion.

---

### Post by DualFusion on 2008-07-10
1) Yes ive looked at the other thread, and thats how i now see the ubuntu installer.

2) yes i have done md5sum check and disk integrity check.

3) ive tried a new IDE cable and still no change.

EDIT: Is it possible to install with one HDD, then once I am done installing, connecting the second HDD with it working properly, as in me (or root) read/write the second HDD?

I am sure the second one works, its has in other computers, is there a certain partitioning scheme I need to assign it? To be on the safe side, I left it as 1 ext3 partition taking up the whole space of the drive.

EDIT 2: To further test the second hard drive, I made it master and the only drive available. I tried the installation again and it worked perfectly. For some reason I guess the installer doesnt want to support to drives.

Thank you,
Kevin.

---

### Post by cariboo on 2008-07-10
Make sure you have your drives jumpered properly, make one the master and the other the slave, I have never had to much luck with cable select.

Make sure that the bios detects two hard drive, it doesn't matter if the size is off. Linux is smarter then the bios:)

Jim

---

### Post by DualFusion on 2008-07-11
Hmm well for some reason one i put the other hdd in as master and the current as slave (same as in the beginning) it worked perfectly, well after several tries from the beginning and reboots.

Thanks everyone,
Kevin. :)

---

