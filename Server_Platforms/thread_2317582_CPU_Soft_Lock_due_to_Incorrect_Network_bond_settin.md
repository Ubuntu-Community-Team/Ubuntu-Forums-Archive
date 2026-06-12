---
title: "CPU Soft Lock due to Incorrect Network bond settings"
date: 2016-03-17
forum: Server Platforms
---

### Post by sawyer2 on 2016-03-17
HI,
I've had an Ubuntu 14.04 LTS server running, and today I've run across an issue after some networking configuration changes. I was trying to create a network bond which was also configured in 2 VLANs. 

Due to my network configuration error, I am now getting a SOFT LOCK error in my CPU when trying to boot. I have tried to access the Ubuntu rescue mode, which also results in that LOCK error. Is there a way to modify the /etc/network/interfaces file without it powered on, from an external device? The system is also setup using an Ubuntu software RAID. 

Thanks.

---

### Post by volkswagner on 2016-03-17
You can boot a live cd and mount the file system if you are using MDADM.

Ubuntu live CD > run DiskUtility > Right Click the volume you want to mount and choose mount > edit your files > reboot :)

---

### Post by sawyer2 on 2016-03-17
Do I need to use the server edition for live CD, or is the desktop version of Ubuntu what you are referring to?

---

### Post by nerdtron on 2016-03-19
Recommended to use the Live CD but you can also use the server edition (albeit a little complicated).

---

### Post by Thirtysixway on 2016-04-23
Use the Desktop iso to boot and modify that file.

But, what options are you selecting in recovery mode?  You should be able to boot it without networking support and fix it.

---

