---
title: "Ubuntu server"
date: 2010-08-21
forum: Server Platforms
---

### Post by heeman453 on 2010-08-21
Hi everyone, I am not too experienced with linux but I managed to set up a server and got it running for over a year now...but now I am stuck..It seems there is some problems while booting up and I get a message like "kernel panic - not syncing - attempted to kill init". A quick search on google explained me a bit what this what all about but I really need to extract data from this hard disk as it was running 2 websites plus I need access to the database. I tried connecting the hard disk to an XP os but then I realised that windows cannot read this type of files.I have found that there are some softwares out there that can operate from a windows platform and read linux files but since I wasted much time already I thought I would post and get some ideas from anyone here...Thanks for reading this post and I hope I can get some help.

---

### Post by TNHarleyRider on 2010-08-21
To simply recover files from your Ubuntu system I would suggest booting the server from an Ubuntu Live CD, then browsing out to the HDD and retrieve the data or files that you need.

---

### Post by CharlesA on 2010-08-21
Boot into recovery mode and see what error it shows before the kernel panic.

Hold shift until the GRUB menu is displayed, then select recovery mode.

---

### Post by heeman453 on 2010-09-06
Thank you, I will try that and will give you an update later on.Again, thanks a lot...

---

### Post by heeman453 on 2010-12-01
> **heeman453 said:**
> Thank you, I will try that and will give you an update later on.Again, thanks a lot...

I have been away for a while, I hope anyone can help here. I have tried booting in recovery mode and whatever previous kernel I tried to boot, I get this message : 

kernel panic - not syncing: Attempted to kill init!
Dumping ftrace buffer: 
(ftrace buffer empty)

Any idea what can be done to solve this? I need to retrieve all these files from this server platform. Thanks for reading, hopefully I will get some help which would save me time digging around.

---

