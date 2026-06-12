---
title: "Error Loading Operating System"
date: 2009-03-25
forum: Server Platforms
---

### Post by Stevie-G on 2009-03-25
Hi guys 

This is my first post I have installed ubuntu server 8.10 on the following:
Dell poweredge server 4400
two xeon 1000mhz proccessors
4gb memory
8 x 36Gb 10k scsi Hard Drive Raid 5

I go through the installation and except the defaults guided the entire disk. then I select Openssh and Samba as services to install remove the disk from the drive the machine reboots and I'm left with a message on the screen "Error Loading Operating System."

Any help would greatly appreciative as I am Ubuntu noob wanting a change from windows.

Thanks in advance

---

### Post by jbrevik on 2009-03-25
I suspect that it has something to do with the raid configuation in the BIOS. First check the BIOS to see if the drives are being detected

---

### Post by jbrevik on 2009-03-25
Also might want to look at this:
[http://ubuntuforums.org/showthread.php?t=1001229](http://ubuntuforums.org/showthread.php?t=1001229)

---

### Post by Stevie-G on 2009-03-25
Thanks jbrevik will try later today

---

### Post by Stevie-G on 2009-03-26
bios detects 1 container 236.58Gb Raid 5 ran Dban re-installed ubuntu noticed that when it sets the ext3 partition it hangs at 33% for about 10mins then moves to the next screen.now after my machine boots all I get is a flashing cursor.

Tried running the install cd the selecting boot for hard drive still get flashing cursor does ubuntu work with raid 5 or do i have to reconfig my raid to raid 1.

Help pleeease

---

### Post by Stevie-G on 2009-03-26
No luck what so ever trying to install ubuntu server 8.10 on Dell PE 4400 have A11 Bios update and Perc 3/Di firmware 2.8.

So I deleted the partition and downloaded 8.04 and went through the install and guess what????????????????????????

Success:biggrin:\\:D/:biggrin:

---

