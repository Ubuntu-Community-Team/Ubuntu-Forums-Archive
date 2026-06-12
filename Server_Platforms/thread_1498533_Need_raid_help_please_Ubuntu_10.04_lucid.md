---
title: "Need raid help please Ubuntu 10.04 lucid"
date: 2010-05-31
forum: Server Platforms
---

### Post by flyboy183 on 2010-05-31
I am currently building a new Ubuntu home media server and I would appreciate some help and advice on a few issues as I am relatively new to Linux. 

System specs:
  mobo - Asus M4A785-M
  cpu - AMD X2 240, 2.8 GHz Dual Core
  ram - 1GB DDR2-1066
  psu - 700W
  os - Ubuntu 10.04 64bit (dedicated 80GB PATA drive)

My goal is to run a 6 TB software raid 5 array using 4, 2TB Hitachi Deskstar SATA drives connected to a highpoint rocketraid 2320 card.  At the moment I am running tests on the array using 3 of the 4 drives and I have the following problems:
 

 
[LIST=1]
[*]When I reboot the computer, I have     to manually start the array  in the disk utility and mount the     volume, how do I automate that process?
[*]I partitioned the array using the     disk utility, created a GUID Partition table, using Ext4, mounted as     a Linux RAID Partition at /dev/md0p1. When I do I get a warning     message that “The partition is misaligned by 506880 bytes. This     may result in very poor performance. Repartitioning is suggested.”      I have tried again, even tearing down and rebuilding the array with     the same result?
[*]Each time I reboot the machine and     manually restart the array, it only runs in degraded mode?
[/LIST]
 

 Like I said, I am new to Linux and would appreciate any help you can give.  Thanks.

---

### Post by reukiodo on 2010-08-01
Several months and no answer...

Did you find your answer elsewhere and/or solve it on your own?

I have this same error.

---

### Post by Ocxic on 2010-08-01
You Have to program/setup the RAID card.. the card itself will create the RAID once it's setup properly. you DO NOT need to create an array with ubuntu or the installer. if you're seeing all 4 drive individually then you've not yet setup the your RAID card. (If your really trying to setup a SOFTWARE RAID then you might as well pull out the card, and connect the drive directly to your computer.)

Once properly setup you will see ONE 6TB drive, when setting up ubuntu that you may partition as your wish.

I think this is a case of someone not RTFM.

---

### Post by cariboo on 2010-08-01
This should have really been asked in the [server section]("http://ubuntuforums.org/forumdisplay.php?f=339"), questions like this get lost in General Help, it probably would have helped if someone had reported it and asked that it be moved.

I've moved it to server platforms.

---

