---
title: "I can't boot from my USB device"
date: 2017-01-28
forum: Windows
---

### Post by Rogerrabbit on 2017-01-28
¡Hi!

 
I have this problem that I want to boot from my usb pendrive (an 8 GB Verbatim) with windows 7 but my Lenovo notebook doesn't do it.
I have tried with the 3 usb ports my notebook has, the 3.0 and the others that are not 3.0 but nothing happens.
My notebook recognize the usb, in fact when I get into the BIOS, the usb appears on the list of devices for booting with its Verbatim name and all but when I try to boot from it nothing happens.

Information:

My notebook doesn't have a CD/DVD device, that's why my only option is using an usb device for installing an OS.

Before formatting this notebook, I had windows 8 installed, now I have Ubuntu 16.04 on it and what I want to install is windows 7 ultimate.

Before doing anything I fomatted my usb device with FAT32 and it's been like that since then and I put my bios in Legacy mode with the booting priority to the usb devices and it's been like than since then.

What's curious is that I have 2 usb devices that are the exact same (the verbatim one) and I created both devices with the same software (Rufus), one usb with windows 7 and the other one with Ubuntu 16.04, and I couldn't install windows 7 because after the intallation started windows told me "There is no booting device, please insert it", or some like that, which is weird because I put the usb, it booted from it, the installation started but then the windows installation couldn't read the usb it didn't matter in what port I put it?!, weird, BUT I could install Ubuntu 16.04 with the other usb device perfectly !!!

After that I decided to format the usb again (in FAT32) and create the windows 7 installer on it again but with ubuntu's startup disk creator, I had to change the extention from ISO to IMG tho, because the startup disk creator won't read it.

After doing that my laptop is not booting from that usb device, it doesn't matter the port I use, I don't know what to do now.

Everything I did and have done was with the usb device formatted in FAT32, with the bios in legacy mode and with the booting priority to the usb devices.

Please help me, I don't know what else to try and I seriously need to have windows installed.

Thank you.

---

### Post by alexeyn on 2017-01-28
rufus can perform efi format  too. check it.second: check usb cd, not hdd

---

### Post by oldfred on 2017-01-28
Moved to Windows sub-forum.

If system was Windows 8, and you installed Ubuntu, is system still UEFI with gpt partitioning?

Windows 7 default installer is BIOS only and you have to modify it to be UEFI boot, if that is what you want. 
Some advantages to UEFI, but you can use the 35 year old BIOS/MBR configuration. 

But if flash drive correctly configured, you must have secure boot off as Windows 7 does not support UEFI Secure boot. And may have to have USB boot on in UEFI. But do not turn on a setting that says Windows or Other as that is really Secure boot. With Windows 7 you have to use "Other".

        How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Convert Windows 7 install to UEFI This user said he need the repair/recovery from his Windows 8 to convert Windows 7
[URL="http://ubuntuforums.org/showthread.php?t=2304736"]http://ubuntuforums.org/showthread.php?t=2304736
[/URL]
 Only 64 bit supported for UEFI boot, Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx) 

[URL="http://ubuntuforums.org/showthread.php?t=2304736"]
[/URL]

---

