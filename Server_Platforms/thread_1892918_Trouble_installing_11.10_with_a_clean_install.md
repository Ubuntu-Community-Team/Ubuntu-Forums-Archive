---
title: "Trouble installing 11.10 with a clean install"
date: 2011-12-09
forum: Server Platforms
---

### Post by gkellison on 2011-12-09
I am trying to do a clean install of the new Ubuntu 11.10 64bit server. Every time it gets to installing select and install software it errors on me. I can't skip it and get GRUB boot loader to install either? I am stumped? I have a gigabyte ga-k8u-939 mainboard with 2 gigs memory that I have reset the bios to default settings. I have tried several different HD's. I have downloaded the OS twice trying both cd and USB thumb drive? I would appreciate any help.

---

### Post by zeljkojagust on 2011-12-09
Could you give a bit more details on errors you receive?

---

### Post by gkellison on 2011-12-09
Going through the installation process either from a cd or a thumb drive it all goes well until the installation gets to the select and install software. The screen will turn orange and it says that a step has been skipped but I can go back to a menu in which I can select to have it try again. I skipped it and tried the GRUB loader and it failed as well saying it couldn't write to target. I have narrowed it down to a problem with this mainboard. I have used the same installation cd and HD's with another mainboard and was successful with the install.

I have also turned of the RAID features on this mainboard.

---

### Post by BC59 on 2011-12-09
When you reach the screen Try Ubuntu-Install Ubuntu, choose try and wait until the system is established. Then post what happened.

---

### Post by zeljkojagust on 2011-12-09
As far as the software installation I would recommend skippin' it in any way (as you can install the software you need after the installation of Ubuntu). And as for Grub installation, did you get the question do you want to install it in the master boot record of your disk (disks if RAID), or you get just the error? If you get just the error, than i presume something is wrong with the disk configuration.

---

### Post by gkellison on 2011-12-09
BC59 - I did not see a screen that would allow me to "Try Ubuntu"? The system boots up the cd where I select a language and then to a menu screen that has the install at the top. I looked in the options but did not see a "Try Ubuntu"?

zeljkojagust - I agree that installing the software is not a problem as I would not select all the software offered if I had gotten to that screen. I am currently working my way back to get the error for the grub loader. Will report when I reach it. The disk configuration is correct (No RAID,  IDE drive set to master by jumper, at the end of the IDE cable for master and into mainboard in IDE1 with only cd-rom on seperate IDE cable into mainboard IDE2) and the same drive was used to install the same os with different mainboard. Same installation cd. Also, have tried 3 other HD's with this main board and get the same error.

Grub loader error - The 'grub-pc' package failed to install into /target/. Without grub boot loader, the installed system will not boot.

---

### Post by BC59 on 2011-12-09
Then read this thread and try to apply the instructions:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by gkellison on 2011-12-09
The "apci=off" didn't do the trick. I am now trying the "nomodeset" option now. Will report.

---

### Post by gkellison on 2011-12-09
No luck with the "nomodeset" option either. It seems that other people are having problems with the grub boot loader as well as I read on the net?

Switching to a SATA hd made no difference. Has to be a Uli M1689 chipset conflict?

---

### Post by zeljkojagust on 2011-12-09
Ubuntu Server doesn't have Try option...

---

### Post by zeljkojagust on 2011-12-09
> **gkellison said:**
> BC59 - Grub loader error - The 'grub-pc' package failed to install into /target/. Without grub boot loader, the installed system will not boot.

... as I said, did the grub installer asked you do you wan't to install it in the MasterBootRecord or select the destination? If you didn't have that question something went wrong with previous steps.

---

### Post by gkellison on 2011-12-09
No, I did not get asked that question.

---

### Post by zeljkojagust on 2011-12-10
Try like this: boot from Ubuntu Server CD, and before you press Install, hit F6 and select Expert Install by hitting space button from the menu that pops out. Go trough every option, manually partition your hard drives and skip the software installation step (go right to Grub boot loader installation). See what happens than.

---

