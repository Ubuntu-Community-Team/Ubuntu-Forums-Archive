---
title: "Ubuntu Server 12.04 install -- READ DMA error"
date: 2015-03-27
forum: Server Platforms
---

### Post by sklpr on 2015-03-27
Hello all , 

Sorry for posting here but since it's about an Ubuntu server installation problem and I am facing some problems I would like  to ask a general question instead of posting a new thread.. 

Does it matter if we try to install Ubuntu server (12.04 64 bit version) on a hard disk (WDC - Red 1TB) via **USB** (using [pen drive]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") ) ***vs*** using a bootable **CD-ROM** ? 

I tried installing via USB but I get : " **READ DMA fail command error** " when booting to it, but it boots and works (get that error as well when I tried to update grub loader after installing XEN hypervisor ) ... 

The reason I am asking this is because I think am going to face problems in the future since it's not a clean installation [without errors] :-/  You guys think the problem is that i am trying to install Ubuntu Server via USB drive and the installation files are corrupted [btw I have used this drive several times to install other operating systems] ***or*** it's hard drive fault ?? 

My system has : Windows 8.1 installed on (C: - ssd drive) and I try to install Ubuntu Server on another hard drive(R: WDC-RED drive) and dual boot  [ I make partions etc.. and reserve space for LVM ]

Thanks in advance !

---

### Post by oldfred on 2015-03-27
Moved to your own thread as issue is different.

I only installed server once a couple of years ago, so I really do not know it. But server is really everything the same without a desktop or gui. And many with server installs, install a lightweight gui, but not all the desktop applications.

Install from USB flash drive is now the more standard way to install. Flash drives are reuseable and many new systems now do not even have cd/DVD.
Did you check that md5sum was correct?
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If system came with Windows 8, that would be UEFI/gpt, or did you install yourself with BIOS and MBR partitions?
And then what brand/model system.
Some systems or motherboards may need UEFI/BIOS settings.
Are drives set for AHCI, not IDE nor RAID?

---

### Post by sklpr on 2015-03-27
Oh okay I  knew it!But I couldn't delete the previous post :-) thank you very much !

The system I am using is a desktop so it came with windows installed (7 but then i upgraded to 8.1 x64 bit) so i guess it has UEFI/gtp

My pc :  
CPU is -- > Intel Core i7 920 @ 2.67GHz
Motherboard -- > Gigabyte Technology EX58-UD5 (Socket 1366)
GPU-- > 1535MB NVIDIA GeForce GTX 580 and 12GB RAM 

I want to clean install on an empty hard drive ( 1TB Western Digital Red if that helps ) Ubuntu server 12.04 x64 bit and then install XEN hypervisor on that ! The reason I do want that is for a University project.. and I am new into Virtualization and servers .. ! 

 I haven't done any change to the hard drive so i guess it's IDE mode but I ain't sure .. This need to be changed and set to ACHI ?? you think that's the problem ? 

Here are some screenshots that I 've taken of the error , not sure if it helps  : [IMG]http://i62.tinypic.com/o7pvm1.jpg[/IMG]

 If you need me to provide further information feel free to ask me :-)

---

### Post by oldfred on 2015-03-27
Many newer Gigabyte boards need IOMMU settings changed in UEFI and perhaps a boot parameter to implement IOMMU in software.
Just because motherboard may be UEFI, does not necessarily mean you have installed in UEFI mode. And Gigabyte was one of the last to add UEFI to its motherboards.

 Gigabytes P67 & H67 hybrid efi -Hybrid EFI is a UEFI based on the open source TianoCore
[http://www](http://www).[rod]("http://www.rodsbooks.com/gb-hybrid-efi/")sbooks.com/gb-hybrid-efi/
[http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html](http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html)
Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by sklpr on 2015-03-28
I changed the BIOS option - > **ATA mode** to *AHCI* because it was *IDE* (I never changed that before) as you pointed me on at first and now i managed to install and boot Ubuntu server and XEN without any errors ;-) 

Thank you so much for the help ! ***problem Solved*** :-)

---

