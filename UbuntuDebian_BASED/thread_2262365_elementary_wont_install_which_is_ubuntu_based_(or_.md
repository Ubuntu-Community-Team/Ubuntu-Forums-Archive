---
title: "elementary wont install which is ubuntu based (or so i was told)"
date: 2015-01-24
forum: Ubuntu/Debian BASED
---

### Post by lewis9 on 2015-01-24
hi im trying to install elementary and i cant seem to get it to install properly i tried it on my laptop and it worked fine but when i try to install on my desktop it just comes up with loads of errors.
im installing from a CD, i downloaded it form the official site, 64bit processor so i downloaded the 64bit version and i was using windows 8.1 (inactivated)  at the time but this has now gone from my hard drive for some reason and i cant reinstall as i only have an upgrade disk 
here is my spec:
MB: Gigabyte GA-970A-DS3P AMD 970 ATX Motherboard
RAM: 8GB (2x4GB) Crucial Ballistix Sport 1600MHz CL9 DDR3 Dual Channel Kit [BLS2CP4G3D1609DS1S00CEU]
Graphics card: MSI Radeon R9 290 Gaming Edition 4096MB GDDR5 PCI-Express Graphics Card 
CPU: AMD (Piledriver) FX-8320 3.50GHz (4.00GHz Turbo) Socket AM3+ 8-Core Processor
PSU: be quiet! Power Zone 850W Full Modular Silent Power Supply
HDD: 1TB Seagate Barracuda ST1000DM003 3.5" SATA III Hard Drive
if you need any more information please ask (i was unsure of what was needed so i just put everything i coould think of into this) as i dont know what to do any more and it is becoming more and more frustrating.
thank you

---

### Post by oldfred on 2015-01-24
Moved to other OS since not Ubuntu.

We are really Ubuntu forum and do not know what differences Elementary has made.

Gigabyte does need the IOMMU setting changed in UEFI.
Are you installing in UEFI or BIOS boot mode?
If Windows 8 pre-installer, you should install in UEFI mode to easily dual boot.

See links in my signature for more UEFI info. But that is for Ubuntu.

---

### Post by lewis9 on 2015-01-24
thank you for the reply i dont know either what the differences are i just didnt get anywhere with the elementary support pages and i was using pressing F12 which made my HDD and optical drive appear plus any USB's installed but i was clicking on the UEFI then my optical drive, also im not trying to dual boot.

---

### Post by oldfred on 2015-01-24
If using UEFI this page is important.

 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by lewis9 on 2015-01-24
i have the american mega trends BIOS  and it is set to UEFI and legacy but ive been click on the SATA PM: ATAPI iHAS124 E (the optical drive) which i assume is the UEFI mode.
forgive me if im being a bit stupid im knew to all of this.

---

### Post by lewis9 on 2015-01-24
my mistake i was booting in legacy mode

---

### Post by buzzingrobot on 2015-01-25
Elementary is based on Ubuntu.  There are currently two versions. Luna is the only actual release, and it is based on Ubuntu 12.04.  Freya is based on 14.04, but it remains in beta. So, knowing which version you are trying to install will help researching these problems.

Installers typically begin formatting the drive(s) as soon as you select which drive and partitions you want to use, and then move on to the rest of the install procedure. The formatting continues in the background.   If your effort to install Elementary got at least that far, and you targeted the installation at the entire disk, the entire disk was formatted. 

(However, the Windows recovery partition may still be there -- it's hidden. You can run the Gparted program after booting a live image to check.  I don't know if it is in the Elementary live image, but it is in the Ubuntu image.)

---

### Post by oldfred on 2015-01-25
Ubuntu's full drive install also erases recovery partitions or everything on drive. 
That is why we always suggest both the writing of the recovery image and a full backup of Windows.
Hard drive will eventually fail anyway, so those are the backups everyone should have.

---

