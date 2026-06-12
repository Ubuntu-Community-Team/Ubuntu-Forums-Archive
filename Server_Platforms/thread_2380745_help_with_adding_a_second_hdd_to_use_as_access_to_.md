---
title: "help with adding a second hdd to use as access to media on server"
date: 2017-12-21
forum: Server Platforms
---

### Post by supah2o on 2017-12-21
Hi there,

I am new to ubuntu server and servers in general, I'm not sure if this is the appropriate place to ask (if not please kindly re-direct me). I have tried extensive googling to try resolve all my issues and have made some progress but with the amount of documentation out there am feeling more lost than ever! 

I am attempting to make a home server and will jump straight in and describe what i've accomplished so far..

I downloaded and installed the latest LTS of ubuntu server (16.04) using a bootable usb onto a 120gb ssd, I have samba installed and a remote desktop client, everything is up and working fine. I then added another 500gb hdd internally and managed to format and mount it to /data in the root directory, but the guide i followed on initial setup showed me to configure the smb.conf file putting the access into the root directory with appropriate folders (which was the 120gb ssd). I would like to use the 500gb that i have for people in my household to access and potentially leave the ssd for just the operating system, how would i go about doing this? (unfortunately not as simple as editing the smb.conf file i found out, to my despair!)

Any help would be appreciated or even a point in the right direction. Please feel free to ask anything if i have not provided enough info.

---

### Post by darkod on 2017-12-21
It is actually as simple as editing the smb.conf file and then restarting the samba services (smbd, nmbd). When you declare shares in smb.conf you select the path where the share should be. If you select the share to use /data (or a subfolder of /data) then all files in the share will be on the HDD and not the SSD.

---

### Post by supah2o on 2017-12-21
Thank you!! You blessed saint! I can't believe it, I was almost there and second guessed myself and didn't restart the service, and when it didnt work went into depression! :D if I want to expand the storage on this at a later stage, by adding another hdd, is it as simple as doing what i already did or would i be better using LVM?

---

### Post by darkod on 2017-12-21
If you want the space of two or more HDDs to be shown as single total space, you have to use LVM. Otherwise the disks will have to be mounted on different mount points (like /data1, /data2) and it will be more complicated to point the same share to it.

If the disk is still empty and new, better to set it up as LVM now which allows you to add easily more storage to it later.

---

### Post by supah2o on 2017-12-21
Okay, I'll do that now then and save myself later hassle, are there any useful resources you could point me towards to set this up? (If not google is my friend :)). Thank you again for your help darkod!

---

### Post by darkod on 2017-12-21
I don't have any links at hand for LVM, it's quite simle so I don't keep them. Google will help you. You can look for Digital Ocean tutorials too, they have some nice ones... Basically any more recent tutorial of LVM will be enough for simple setup.

---

### Post by supah2o on 2017-12-21
Awesome! I will have a look and get on it. All the best and hope you have a great New Year fella!

---

### Post by oldfred on 2017-12-21
I do not know nor use LVM, but have some links, I think may still be current as LVM has not really changed.

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)
[https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm)
[https://linuxconfig.org/linux-lvm-logical-volume-manager](https://linuxconfig.org/linux-lvm-logical-volume-manager)
[https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)
Manually create
[http://community.linuxmint.com/tutorial/view/2061](http://community.linuxmint.com/tutorial/view/2061)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://askubuntu.com/questions/470632/install-lvm-dual-boot-with-windows](http://askubuntu.com/questions/470632/install-lvm-dual-boot-with-windows)

---

### Post by supah2o on 2017-12-21
Ah wow oldfred, that's great! Will definitely have a look through these and hopefully do it right and not blow up my tower!

---

