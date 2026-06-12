---
title: "Windows7 is missing in GRUB2. How can I repair it?"
date: 2014-06-11
forum: Windows
---

### Post by paleomariomm on 2014-06-11
Hi. First, I am going to explain the partitions I had before the problem appears. I have a MacPro with basically three partitions: Windows 7, Macintosh and the previous Linux Mint 13. When I switched my computer on, the GRUB showed me the three operating systems. This morning I decided to upgrade to Linux Mint 17 by doing a fresh installation with a DVD and formatting the previous Linux Mint partition to introduce LM17. Up to here I think it is easy to understand.

Let's start complicating the events. I installed successfully LM17. I reboot my computer and here is the surprise: GRUB2 only shows Macintosh and LM17, but no trace of Windows7 partition.

More data. Rebooting the MacPro and holding pressed the Alt key button during the initialization, it is possible to access to the different partitions following the MacPro method (not using GRUB). In this case, I can see only Macintosh and Windows7. Moreover, when I click on Windows7, appears: grub rescue!!!!!!

I already know that all the files in the Windows partition are there. When I start LM17, I mount it and can see all the files that are part of Windows, including my own folders in the Desktop.

So, what do I want? Well, I would like to switch my computer on and have the possibility to choose which operating system I want to use: Mac, Windows, LM17.

Thanks in advance and hope anybody from this enormous community could help me.

---

### Post by yancek on 2014-06-12
You could try booting Mint and from a terminal, run:  sudo os-prober
When that finishes, run:  sudo update-grub
I've never used a mac but this would work on a standard pc.

---

### Post by kc1di on 2014-06-12
Hi paleomariomm and welcome to Ubuntu forums.  

If Yancek method does not work for you you may want to try Boot-Repair. 
you can find it [here.]("https://help.ubuntu.com/community/Boot-Repair")  Follow the direction on the page.

---

### Post by kc1di on 2014-06-12
Hi paleomariomm and welcome to Ubuntu forums.  

If Yancek method does not work for you you may want to try Boot-Repair. 
you can find it [here.]("https://help.ubuntu.com/community/Boot-Repair")  Follow the direction on the page.

---

### Post by onapthanh on 2014-06-13
I have the same and I think that all the files in the Windows partition are there. When I start  LM17, I mount it and can see all the files that are part of Windows

---

### Post by Nobody Nessie on 2014-06-18
Maybe, have a try with grub-customizer ?

---

### Post by oldfred on 2014-06-18
I also do not know Mac.

I do not think grub customizer works with a Mac and boot issues. It is more for custom configuring grub.

Is Mint in UEFI or BIOS boot mode?

Everything I have seen is that with a Mac you have Windows in BIOS boot mode even thought the Mac uses an older UEFI. And it is better to install Linux in UEFI boot mode.

Many with Mac use rEFInd.
       Alternative to grub using refind or gummiboot
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards](https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards)
Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

 [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
 MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

 Triple Boot MacbookPro (Lion, Win7, Ubuntu) Ubuntu in BIOS mode
[http://ubuntuforums.org/showthread.php?t=1908210](http://ubuntuforums.org/showthread.php?t=1908210)

---

