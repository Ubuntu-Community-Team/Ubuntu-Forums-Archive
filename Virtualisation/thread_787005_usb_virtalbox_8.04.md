---
title: "usb virtalbox 8.04"
date: 2008-05-08
forum: Virtualisation
---

### Post by gavshouse on 2008-05-08
hi i have looked at other threads of usb problems i cant seem to find one that matches my error msg

any ideas my usb keybaord & mouse is working btw but my Western Digital Ext HDD 250gb (mybook) isnt also i am wanting to plug my ipod in for syncing with itunes later. 

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
0x00004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {f95c0793-7737-49a1-85d9-6da81097173b}

---

### Post by brazh on 2008-05-08
Maybe, this will help you:
> USB on Ubuntu/Gutsy: Ubuntu removed support for /proc/bus/usb/*. We will address this issue in the future. Until this, edit the script `/etc/init.d/mountdevsubfs.sh and activate the four lines around line 40 (Magic to make /proc/bus/usb work). Then execute

/etc/init.d/mountdevsubfs.sh start

From now on, there should be a directory /proc/bus/usb/ and the device entries below should be accessible by any user.

I found it at [http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)

---

### Post by gavshouse on 2008-05-08
right its sort of working

check the image

---

### Post by gavshouse on 2008-05-09
i have it working fine now

---

### Post by IncadudeF on 2008-05-13
How did you fix it. I have the same problem.

---

