---
title: "Create a bootable Windows 7 USB"
date: 2016-05-29
forum: Windows
---

### Post by CFG1324 on 2016-05-29
I have been using this guide to create a bootable Windows 7 USB installer from ubuntu:

[http://onetransistor.blogspot.com/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.com/2014/09/make-bootable-windows-usb-from-ubuntu.html)

Basically the steps are,
[LIST=1]
[*]Create a GPT partition table 
[*]Format to Fat32 
[*]Copy the windows files from the ISO 
[*]Copy the boot folder from /efi/microsoft/ to /efi 
[*]Copy the /1/Windows/boot/efi/bootx64.efi file to /efi/boot from install.wim 
[/LIST]

Additionally, I have tried to format the drive to Fat32 with a GPT partition table and use unetbootin to create the bootable drive. 

I can get my computer to boot from the USB, but I get the following error. 

```
Windows Boot Manager

Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

1. Insert your Windows installation disc and restart your computer.
2. Choose your language settings, and then click "Next."
3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer manufacturer for assistance

Status: 0xc000000f

Info: An error occurred while attempting to read the boot configuration data.
```

I have tried both the windows installation disks that I own and multiple USB drives with the same result. It seems to me that the computer is trying to boot into windows as if it was an already installed system rather than the installer itself. I do not have a CD drive so I need to use a USB.

I have ubuntu 16.04 installed with grub. My computer is set to boot with UEFI. I've tried everything I can think of to fix the error. Has anyone encountered anything similar? Thanks.

---

### Post by oldfred on 2016-05-29
This has similar instructions, do not know if details are different?
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)

---

