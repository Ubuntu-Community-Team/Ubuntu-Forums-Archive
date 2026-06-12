---
title: "Hot swap"
date: 2010-07-04
forum: Server Platforms
---

### Post by Evileendje on 2010-07-04
Hi there,
 
Im using Ubuntu 8.04 64bit server
 
After one of my harddisks died i decided to switch to a raid 5 setup and a hot swap disk. 
 
I installed a hot swap drive in my server and put in a 1T harddisk for test purposes. 
 
When i put in my drive at setup it shows in devices and when mounted it works great. But when i de-mount the drive and take out the drive the /dev/ list doesn't update. 
 
I have scsitools installed and i used scsi-spin to spin down the drive and tried to use the script "[FONT=Calibri][SIZE=3]rescan-scsi-bus.sh" to rescan the /dev list. [/SIZE][/FONT]

[FONT=Calibri][SIZE=3]When i put in a new drive and use the rescan script, the new drive isn't show in the script output. [/SIZE][/FONT]

[FONT=Calibri][SIZE=3]What is it that im missing? And is there a way to automaticly rescan the devices when i hot swap the drive? [/SIZE][/FONT]

---

### Post by Vegan on 2010-07-04
That is not the way hotswap is supposed to be used. Its meant to be able to replace disks in a RAID without taking the server down. It does needs cards that support hot swap as there is some firmware needed.

---

