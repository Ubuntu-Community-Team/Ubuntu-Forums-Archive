---
title: "Will Ubuntu 14.04 LTS support Wubi or a similar method"
date: 2014-03-03
forum: Ubuntu Development Version
---

### Post by sonyboyj on 2014-03-03
i have been trying different methods to dual boot Ubuntu and Windows 7 i tryed the along side windows option PC just boots into windows and i tryed Something else option like 3 times doing different things still boots into windows never asks hey would you like to try linux its like my PC in anti-linux. Wubi is the only thing i havent tryed but i know 14.04 is next month so will it support wubi or a similar method i dont wanna use a virtual machine as there laggy

---

### Post by Gavin77 on 2014-03-03
Wubi is discontinued and only supports 12.04 LTS.
[http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

---

### Post by oldfred on 2014-03-03
These are now older but the process is still the same. Just install to a larger flash drive (8GB or more) as a second boot device. May not be speedy but works, unless system is so old as to not boot from USB port.

 HOW TO Avoid Wubi & Install Ubuntu 10.04 on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

   HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)

   Ubuntu Installation to a USB Stick
[http://www.systemateka.com/usbboot.html](http://www.systemateka.com/usbboot.html)

---

### Post by grahammechanical on 2014-03-03
You may find that Wubi.exe is still included in the 14.04 ISO image. It is there for those versions of Windows that Wubi.exe is compatible with. We are told that Wubi.exe is not compatible with Windows 8.

Do not expect Microsoft to provide a boot manager that recognises any other OS and than those from Microsoft. So, in that sense your machine is indeed anti-linux. But we do have boot repair. And Grub will recognise the existence of a Windows boot loader and list it in its boot menu.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards

---

### Post by sonyboyj on 2014-03-03
> **grahammechanical said:**
> You may find that Wubi.exe is still included in the 14.04 ISO image. It is there for those versions of Windows that Wubi.exe is compatible with. We are told that Wubi.exe is not compatible with Windows 8.

Do not expect Microsoft to provide a boot manager that recognises any other OS and than those from Microsoft. So, in that sense your machine is indeed anti-linux. But we do have boot repair. And Grub will recognise the existence of a Windows boot loader and list it in its boot menu.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards

I tryed boot repair but it didnt work i may try again once 14.04 comes out but i tryed like 5 times in the last 24hrs im a little ticked right now my pc wont except linux. is there a way to make my pc not Anti-linux lol. and is there a good guide to use to dual boot Ubuntu and Win7.;)

---

### Post by Bucky Ball on 2014-03-03
Did this recently, but with a totally empty disk.

Booted to a Live session from the install media (DVD/CD/USB) and created a 40Gb NTFS partition (must be primary), left the rest as an extended partition (used Gparted).

Booted from Win7 64bit disk and installed to that first 40Gb partition, first drive (sda1). 

Boot from the Ubuntu installer and installed Ubuntu to logical partitions inside the extended. In the process I created a 90Gb NTFS partition called 'Share' to share data between Win7 and Ubuntu.

Booted a 64bit Boot Repair USB stick, ran 'Recommended Repair', all sweet. Running faultlessly. Hope that is of some help.

---

