---
title: "VirtualBox - External USB HD detected but not available in disk mngmt (VB XP)"
date: 2008-01-24
forum: Virtualisation
---

### Post by notsu on 2008-01-24
I have a 160gb WD SATA 2.5 hd attached via a USB 2.0 port in VB 1.5.4 (Ubuntu 7.10 host, Win XP guest with sp2). I have enabled the USB support in VB and selected the usb devices in the filter list. I have also followed the instructions on the user manual on page 117, Section 11.4.6 "USB not working". Here's my problem. 

1.) I started up the VBXP and inserted the usb hd. The "safely remove hardware" icon appears immediately but it doesn't have a drive letter. When I go into Disk Management the external drive is not shown. I can assure that this drive is working perfectly fine on a native (non-vb) XP installation on another laptop that I have. 

2.) When I left-click on the "Safely remove hardware" icon and select the entry, it shows a "it is now safe to remove..." message but the external hd is still spinning. Whereas, on a native XP machine, the hd will spin down as soon as I chose to remove the device by using the icon in the system tray. 

3.) I have tested this VBXP with a 4gb Sandisk thumb drive and the icon in the system tray DOES show a drive letter and it can be found in the Disk Management. 

So in the simplest terms, my 4gb thumb is working fine in the VBXP but my 160gb wd hd only activated the "safely remove hardware" icon but it doesn't show up anywhere else. 

Any ideas?

---

### Post by dark_phantom on 2008-01-24
While I have not particularly used the USB support, I am able to mount any USB disk that I have connected.  Try using the share folders option, that's what I use.  Share your drive(s) that way, for example you can share /media/disk for an usb disk.  Then, in wondows map that drive by mapping a network drive using the \\vboxsvr\disk.  Use your id and passwd and you should be able to see that disk.  Look at the 4.4 section on the manual.  I hope this helps.

---

### Post by notsu on 2008-01-24
Thanks for the advice. This is actually the solution I am using to get around the problem. However, I would like to know how I can attach the usb hd directly via usb in the VBXP machine.

---

### Post by dark_phantom on 2008-01-24
[http://ubuntuforums.org/showpost.php?p=4074968&postcount=4](http://ubuntuforums.org/showpost.php?p=4074968&postcount=4)

---

### Post by notsu on 2008-01-25
Thanks again for the reply. The only thing is I am using 1.5.4 and the link is for 1.5.2. Support for USB 2.0 was added to 1.5.4. Also, I have no problem using my thumb drive via USB. Only the 2.5 WD hd is giving me trouble. Anyway, I will try these instructions no matter what and see if it fixes the problem. Thanks!

---

### Post by dark_phantom on 2008-01-25
To make it easier, just install the non open source edition.  You probably have the OSE which doesn't support USB, the full version does.

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by notsu on 2008-01-26
> **dark_phantom said:**
> To make it easier, just install the non open source edition.  You probably have the OSE which doesn't support USB, the full version does.

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

I am using the non open source edition =D

---

### Post by dfmalh on 2008-04-18
Hi, I exactly the same problem.

I have a 120gb SATA 2.5 USB HD attached via a USB 2.0 port in VB 1.5.6 (Ubuntu 7.10 host, Win XP guest with SP2). I have enabled the USB support in VB and added/selected the USB devices in the filter list. 

The USB HD is two partitions, one NTFS (for the large files, e.g. VB backup), and one FAT32. My USB HD is detected on a normal WinXP PC, but not in WinXP guest through VB.

I have done the setup with and checked with a 1 GB JetFlash USB stick, and I have no problems detecting it and accessing it.

Any help would be greatly appreciated.
Thanks

---

### Post by dfmalh on 2008-04-18
**Update**

Figured it out after I read some more post on more forums.

My USB disk works fine with the USB 2.0 setting enabled, but my USB SATA HD (NTFS/FAT32) does not show up in Explorer. Although it showed that the connection was made, and I can remove the hardware... weird :confused:

I then disabled the USB 2.0 support in the settings of my Virtual Machine. After boot up, I could activate the USB HD and after about 25 seconds the NTFS drive would show up, 2 min later I could also access my FAT32 drive. 

_Bottom line_:* disable USB 2.0, and wait 2min30sec after activating the USB HD.*

:lolflag:

---

