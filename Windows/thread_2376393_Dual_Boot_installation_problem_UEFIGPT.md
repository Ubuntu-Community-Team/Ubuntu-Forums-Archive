---
title: "Dual Boot installation problem UEFI/GPT"
date: 2017-11-02
forum: Windows
---

### Post by tarecco on 2017-11-02
Hello everyone

I have a problem here with my dual boot installation that is driving me insane!

I bought my laptop with windows 8 installed, that I upgraded to Win10, and installed as dual boot Ubuntu 16.04. I don't really like win10 (who does?), but I need to have a windows OS installed for specific programs that don't have a Linux distribution yet, like Corel Draw, Illustrator, etc.. So, I deleted the data on the WinOS partition, and tried to install a fresh copy of Win7 64bit. This is where the problem lies. I created a bootable USB with WintoUSB, and if I try to run it from the UEFI, tells me 

[I]Windows Failed to Start.  A recent hardware or software change might be the cause.  To fix the problem:
[/I]
*1. Insert your Windows Installation disc and restart your computer.*

*2. Choose your language settings, and then click "Next"*

*3. Click "Repair your computer"*
*If you do not have this disc, contact your system administrator or computer manufacturer for assistance.*
*File: \EFI\Boot\BCD*

*Status: 0xc000000d*
[I]Info: The Boot Configuration Data for your PC is missing or contains errors.
[/I]
I googled millions of pages already, all of them tell me to disable Secure Boot (It's disabled) and Enable Legacy Mode. My board doesn't have this option, only the option to disable UEFI. When I do disable UEFI boot, it runs BIOS and launches the USB boot, but then, when I want to select the partition to install:[I]

Windows cannot be installed to this disk, the selected disk is of the GPT partition style.

[/I]Is there any other way I can install Win7 on my machine without having to format the whole disk and lose my Ubuntu setup?Thank you all

---

### Post by yancek on 2017-11-02
According to the microsoft site at the link below, you need to delete the efi partition for it to boot in the MBR mode.  If your windows 10 and Ubuntu are/were both efi, you will not be able to boot Ubuntu as it's boot files will be on that efi partition.  Windows 8 & 10 default installs use UEFI/GPT while 7 was MBR.  I would think you should have  a CSM/Legacy option in the BIOS.  

.  [https://technet.microsoft.com/en-us/library/hh825112.aspx](https://technet.microsoft.com/en-us/library/hh825112.aspx)

---

### Post by oldfred on 2017-11-02
Better to convert Windows 7 installer to UEFI.
You have to copy DVD to flash drive and move/rename a couple of files.
UEFI only boots from /EFI/Boot/bootx64.efi which the Windows 7 installer does not have.
You do have to have 64 bit Windows and Windows 7 does not support UEFI Secure Boot.

        How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI. 

If you really want the 35 year old BIOS/MBR configuration you have to convert drive from gpt back to MBR(msdos). 
You can do that with sgdisk, but have to install the grub-pc for BIOS boot as you have the UEFI boot version of grub.

Windows only boots in UEFI mode from gpt.
Windows only boots in BIOS mode from MBR(msdos).

---

