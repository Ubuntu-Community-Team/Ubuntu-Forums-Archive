---
title: "Got a question about Ubuntu Server (no GUI except webmin) with USB EX 2 Nas"
date: 2013-09-29
forum: Server Platforms
---

### Post by jaime3 on 2013-09-29
Howdy all. I have a Dell PowerEdge 1850. So it has USB 2.0. Yes I know slow. But I have one TB usb 2.0 external drive and other 2 that is usb 3.0. Ofcourse wont run full speed max on my server is 2.0. There is two bay on server for HDD one is os other is empty. Anyway's can I use WEBMIN for hooking up my usb external 
that is already partition? Probaly all NTFS. I would be sharing these over network to WD Live Tv, and to other laptop running Windows and Linux. Basically making this a NAS. Ty guy's. Oh Yes I'll be accessing from android devices to view movies or so forth. TY

---

### Post by Lars Noodén on 2013-09-29
If you're making a NAS to share over your LAN, then you could look at Samba or SSHFS.  If you want access over the wild Internet, then you should look at SSHFS and forget Samba. 

Either way, you'll want to use a proper file system like EXT, such as EXT4 and leave NTFS alone.  It does a very poor job in general and is missing a lot of the basic support needed in a Linux file system.

---

