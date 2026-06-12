---
title: "Can't install/boot windows via USB in Linux Mint environment"
date: 2016-08-17
forum: Windows
---

### Post by creation-babu on 2016-08-17
I am using Linux Mint 17.2 in my HP Envy. I want to create dual boot system in my laptop, windows 8 with linux mint. For that, I want to clean install Windows 8 and reinstall Linux mint as dual boot. But, I cannot boot my bootable USB drive with Windows 8. I tried all the boot options entering BIOS system. I cannot even get into GRUB (hit and hold SHIFT key while booting) to enter into recovery mode. How do I proceed. I want to remove Linux and put Windows in my laptop and reinstall Linux as dual boot. Please help me here.
Thanks

---

### Post by oldfred on 2016-08-17
Moved to Windows sub-forum, but perhaps Mint?

How  do you boot system UEFI or BIOS.
And are you booting Windows installer in same mode?

Windows only boots in UEFI mode from gpt.
Windows only boots in BIOS mode from MBR.
So you must boot installer in correct mode to match partitioning or desired booting method.
And Windows does not correctly convert a gpt partitioned drive to MBR(msdos) leaving backup gpt partition table.

Is your Windows installer a recovery from original install or totally new new ISO?
And if not a legal download from Microsoft we cannot help you.

---

### Post by creation-babu on 2016-08-22
I don't know much. I am running Linux Mint. I have legal new copy of windows 8.1 and have product key. This laptop was pre-installed with windows 8 and I downloaded the product key embedded in UEFI. Now I am trying to install via bootable USB and CD (trying both) but it is unable to boot. I changed the booting preferences through BIOS settings. I don't know how to boot Windows in UEFI or BIOS, all I know is, it should boot usb and install windows. I installed and run boot repair and it says boot successfully repaired. I got this url after boot repair ([COLOR=#b22222]http://paste2.org/7Ypwd1ww[/COLOR]). I got this message after boot repair ([COLOR=#000080]The boot files of [The OS now in use - Linux Mint 17.2 Rafaela] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))[/COLOR][COLOR=#ffd700].[/COLOR] I tried restarting but didn't work.

---

### Post by oldfred on 2016-08-22
If newer UEFI system ignore warning from Boot-Repair on far from start. That is for some older BIOS IDE systems where BIOS was limited to boot from first 137GB of drive. May also apply to some newer systems booting from USB drives.

You do not need product key, but it is really only for the OEM version. With Product key in UEFI, it is automatically used.
       Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

---

### Post by creation-babu on 2016-08-23
I don't understand a thing you said. OK, I don't need product key, but how do I install windows? How do I even boot?

---

### Post by oldfred on 2016-08-23
Most HP use same set of keys to boot. And if UEFI fast boot is on, you have to cold (power off) reboot, not warm reboot from system running. And some laptops require battery to be removed & power switch held for 10 sec to fully drain power to get a full cold reboot. And then you must immediately press correct set of keys to get into UEFI/BIOS.

 [http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook](http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook)
Some HP will not boot a flash drive that is gpt partitioned.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260)
HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)
HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)
Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 Details
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by Wadim_Korneev on 2016-08-24
I had Windows 7 installed with 3 partitions on it. Later I installed Linux on it in dual boot mode. I changed the partition and kept around 100 GB of total 320 GB for Linux installation. In the course of time, I upgraded to Windows 8 and subsequently to Windows 8.1. I never had to face the problem of Windows 8&#8217;s secure boot thingy. It is just to clarify that this process does not show you how to deal with UEFI

---

