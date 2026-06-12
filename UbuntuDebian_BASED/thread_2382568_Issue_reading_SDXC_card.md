---
title: "Issue reading SDXC card"
date: 2018-01-15
forum: Ubuntu/Debian BASED
---

### Post by bluenova on 2018-01-15
I have a new SDXC card (Sandisk Extreme Pro 64GB) for my camera, the camera has formatted it as EXFAT. I'm running KDE Neon 5.11 (Ubuntu Xenial) on a Lenovo Z580 with built in SD card reader.

Initially it couldn't mount the card and I discovered I needed to install exfat-fuse and exfat-utils which I did and then rebooted. It now mounts the card and I can see the contents but the preview images are not complete (partly grayed out) and when opening a CR2 (Canon RAW file) in Darktable it errors saying there is missing information. Opening an image in Gwenview shows part of the image and the rest looks corrupted. I've checked the card again in the camera and I can see all the images without issue so I don't think the card is corrupted.

dmesg reports:
[  173.523523] mmc0: new ultra high speed SDR50 SDXC card at address aaaa
[  173.557792] mmcblk0: mmc0:aaaa SP64G 59.5 GiB 
[  173.561217]  mmcblk0: p1
[  201.531091] mmcblk0: error -110 sending stop command, original cmd response 0x900, card status 0x900
[  201.531093] mmcblk0: error -110 transferring data, sector 69888, nr 256, cmd response 0x900, card status 0x0

The last 2 errors repeat.

I've tried searching error -110 but haven't been able to find anything, any help would be appreciated.

---

### Post by QIII on 2018-01-15
Moved to Ubuntu/Debian BASED

---

