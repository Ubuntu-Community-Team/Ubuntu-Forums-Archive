---
title: "Dual boot with 14.04 and Windows 8.1"
date: 2014-03-13
forum: Ubuntu Development Version
---

### Post by Lodmot on 2014-03-13
I can confirm that it is indeed possible to dual boot Windows 8.1 and Ubuntu 14.04. However, the grub menu is very wonky, I can't seem to use it. And Ubuntu only boots up in CSM/Legacy BIOS mode.  So to boot up in Windows 8.1, I have to go to the "BIOS" settings menu (I don't know what they call it now on newer motherboards) and switch it to UEFI mode. To boot up Ubuntu 14.04, I switch it to "CSM" mode. This is on a Toshiba Satellite P50T.

Anyone else have the grub menu working correctly? o:

---

### Post by oldfred on 2014-03-14
Moved to Ubuntu+1

Other Toshibas but not with new 14.04

       Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

