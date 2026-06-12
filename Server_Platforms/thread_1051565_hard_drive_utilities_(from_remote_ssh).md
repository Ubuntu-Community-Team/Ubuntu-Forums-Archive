---
title: "hard drive utilities (from remote ssh)"
date: 2009-01-26
forum: Server Platforms
---

### Post by gtfourdreams on 2009-01-26
are there any tools (other than fsck) to check the integrity of a SCSI drive? if it makes a difference, these are 9.1gb SCA 80pin hot-swap mounted in a hot-swappable backplane. i put one in, i do a scsiadd, the drive shows up. now what do i use to evaluate the fitness of the drive? 

i have used smartctl to check the s.m.a.r.t. status. i want to do a surface scan and perhaps do some random writes to make sure the drive will be usable in the server. i have about a dozen of these drives that i am trying to go through.

i don't want to have to boot/reboot the system each time with a cd-rom option (like hitachi fitness test). the other reason is because it is a headless server, so that means i would have to run some extra long KVM cables over or physically move the server.

---

### Post by ac7ss on 2009-01-26
tune2fs and e2fsck are both tools to use, you shouldn't use them with a mounted filesystem, so you either have to run them from a boot CD or from another partition. 
Use the 'man' command to learn how to use them.

---

### Post by gtfourdreams on 2009-01-26
thanks but no thanks. i already tried that method. it gives me super block errors. i don't know how to get pass that. (yes, i tried supplying random super block numbers)

i was using ubuntu on /dev/sda and doing diagnostics on /dev/sdb...x so it should have worked.

anyways, i used this tool from seagate. its sufficient for what i needed to do.

> Legacy tools (Seagate drives only):

SeaTools Enterprise Edition
Ideal for SCSI or Fibre Channel drives in servers and workstations. Tests multiple drives simultaneously and sequentially. This version does not test ATA or SATA.

    * Features: Eliminates downtime in your Linux and Windows server environments
    * Access: Download the Windows version or the Linux Command Line version
    * Compatible with Linux and Windows XP/2000/NT/Me/98/95
    * Download sizes: Windows - 2.8 MB, Linux Command Line - 230 KB
    * Learn More about SeaTools Enterprise
    * See the tutorial on the usage of SeaTools for Enterprise.

Download SeaTools Enterprise Now!
Windows Version 	Linux Command Line Version

Download and un-tar and ./execute
[http://www.seagate.com/www/en-us/support/downloads/seatools/](http://www.seagate.com/www/en-us/support/downloads/seatools/)

(sudo the following commands, and apt-get scsiadd and smartctl if you need them)
'scsiadd -s 1' to add the drives (1 = my scsi host)
'./st -l' to get a list of drives
'./st -i /dev/sg3' for information (sg3 = the drive id from command above)
'./st -t 100% /dev/sg3' to run the test (change the 100% if you want a shorter test)
'smartctl -a /dev/sdc' to check S.M.A.R.T. if you so desire

good luck.

---

