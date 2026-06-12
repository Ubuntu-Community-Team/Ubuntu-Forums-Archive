---
title: "troubleshoot micro sd card in adapter not showing up in nautilus?"
date: 2012-11-05
forum: System76 Support
---

### Post by jwyman on 2012-11-05
hi, sorry if this q is naive, but I am using system76 pangolin performance laptop, I slide micro sd card adapter into sd card slot on left front side, then I boot, then I do not see the micro sd card files anywhere

are they supposed to be a subdir of /dev or /media ?

do I have to manually execute mount?

is it a known prob w/adapters rather than actual sd card? does it matter that the micro sd was fmted in smart phone?

do I need to edit /etc/fstab ?

is reader supposed to show up in lspci?

is /var/syslog supposed to show some trace of the inserted sd card being detected? no lines seem to be written to the log tho either when I insert the card while the laptop is running, or after booting with the card already in the slot before power-up

thanks for any help

---

### Post by isantop on 2012-11-06
> **jwyman said:**
> hi, sorry if this q is naive, but I am using system76 pangolin performance laptop, I slide micro sd card adapter into sd card slot on left front side, then I boot, then I do not see the micro sd card files anywhere

are they supposed to be a subdir of /dev or /media ?

do I have to manually execute mount?

is it a known prob w/adapters rather than actual sd card? does it matter that the micro sd was fmted in smart phone?

do I need to edit /etc/fstab ?

is reader supposed to show up in lspci?

is /var/syslog supposed to show some trace of the inserted sd card being detected? no lines seem to be written to the log tho either when I insert the card while the laptop is running, or after booting with the card already in the slot before power-up

thanks for any help

How old is your Pangolin? If it's a newer one, try re-running the System76 Driver.

---

### Post by gordintoronto on 2012-11-06
Card readers are almost always USB devices, so it should show up in lsusb.

What smartphone was the card formatted in? Do you know what format was used, such as fat32? How big is the card (eg. 4 GB)?

When I insert an SD card, it shows up on the left side of Nautilus, showing something like "4 GB". It also appears in /media, but that's the hard way.

---

### Post by jwyman on 2012-11-07
thanks, I updated the system76 driver from 3.0 to 3.2 on my panp9 laptop and restored the system via the icon for system 76 in System Settings
now when I slide in my sd card adapter a nautilus window automatically opens and the files on the card show up under media directory as described, so my problem is resolved

---

