---
title: "XP Not Booting up, Win &amp; Ubuntu can't fix MBR"
date: 2015-05-17
forum: Windows
---

### Post by mark.giblin on 2015-05-17
If I begin back in October last year, my Computer shut down without giving any error, the following day I come to boot up and the machine stalls at the blue windows loading screen.

I tried safe mode, last know working, I tried the recovery software that was supposed to be on a partition on the drive but was missing... The windows recovery disc said it had fixed the problem, it still wouldn't boot.

I installed Ubuntu to an external device and made a backup of the drive to an image file and I was able to mount the partitions of the image.

The SSD manufacturer (Kingston) suggested that I do a secure erase on the drive and re-image the drive and if it works the problem was physical and bad blocks on the drive and doing a secure erase will over write all writable and on formatting again the drive would have all bad blocks marked and replaced. I downloaded Hirens CD. Although the image burn was good and it verified both with the write and checksums, it was a coffee cup coaster claiming that the PXE was missing at first run. 

I tried various attempts to either find how to fix the drive or the image file, so I bought a HDD to replace the SSD and imaged the HDD and tried booting, this time it got a bit further, stalling and telling me that hal.dll was missing, research shows that hal.dll missing claims are MBR related.

Ultimately the need is to get windows up and running so I can use my software and so I can dual boot the machine, until then its pointless me doing anything in the Ubuntu install quarter other than use this install I am currently using.

So what next? Does anyone have any ideas on where to go from here and suggestions of a fresh install are not an option, I have lots of data and programs that I downloaded and paid for on that drive and I can't use them or access data unless the drive boots or the drive image can be used in Virtual Box, only problem there is the drive image is ssd.img and Virtual Box won't accept it not an extension name change or append.

---

### Post by monkeybrain20122 on 2015-05-17
Let it die. XP is dead and should have been buried long time ago. Doubt that you would get any support even on Windows forum.

---

### Post by juansb on 2015-05-28
Why aren't you able to unzip or to move the image ?
You said that you've made a LIVE Usb stick? use it to transfer your files to something external of your computer.
I recommend you get an external high capacity disk to transfer all your files as a back up, and if it isn't possible then try to connect your computer parallel with another pc in a healthy state via LAN network and to transfer the image or the files to the other computer.

A freshly installation of XP is needed, because is not longer supported and to get a precise help for that should be difficult. But be aware of the table partition to don't erase accidentally the dual boot.
I hope you have all the installers of your software? I'm not sure if is possible to backup the registry of Windows via File manager and how to restore it but you could research a bit ;)

By the way, I have a LinuxMint OS modified as a XP ;)
[ATTACH=CONFIG]262273[/ATTACH]

Good luck!

---

