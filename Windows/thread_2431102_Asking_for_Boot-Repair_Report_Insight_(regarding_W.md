---
title: "Asking for Boot-Repair Report Insight (regarding Windows10 boot error)"
date: 2019-11-11
forum: Windows
---

### Post by and02 on 2019-11-11
Hi all, thank you again for reading this post. 

A quick background on the situation. 


[LIST]
[*]Windows  has blocked most of my workarounds( does not load in any safe mode  options, restore points result in error, repair disk and all advance  options have failed)
[*]Windows does not boot from my "Windows Media USB" to reinstall or repair windows.
[*]Windows is in Boot Loop w/ "Critical Process Died" error
[*]I'm booting Bionic Linux of a USB drive to either repair disk or transfer files to external drive so I can wipe out Windows. Either way I'm stuck. looking for other workarounds.
[/LIST]

Open to all suggestions and here is the provided report from Boot Repair (if it helps) [http://paste.ubuntu.com/p/sPpFj2PFtW](http://paste.ubuntu.com/p/sPpFj2PFtW)/



Thank you for your time and good day,

---

### Post by wildmanne39 on 2019-11-11
*Thread moved to **Windows a more appropriate sub-forum**.*

---

### Post by yancek on 2019-11-12
Boot repair is meant to repair Linux systems boot but in some situations, may enable booting windows.  Your boot repair output shows you have windows code in the MBR and that you have an EFI partition with windows boot files.  It also shows the disk on which you have windows is GPT so it will only boot in EFI mode.  Check your BIOS firmware on boot and look for an option to disable Legacy/CSM boot.

You haven't really given specifics on what the problem is.  Did your windows simply stop booting?  What exactly happens, do you see any warning/error messages on boot?  What happens when you try to boot your windows media usb?  Do you get the 'boot loop' when trying to boot the installed windows or when you try to boot the usb?  or both?

Since you only have windows and a windows problem, I would suggest you would have better luck posting your problem at a windows forum or going to the miscrosoft support site.

---

### Post by oldfred on 2019-11-12
You have an UEFI system & UEFI install of Windows.
You should always be booting in UEFI mode.
Not sure how you got a BIOS boot version of Windows in gpt's protective MBR. Boot-Repair will put a syslinux boot loader if Windows is BIOS boot, but does not fix Windows otherwise.

I agree with yancek, check UEFI settings & make sure you only boot in UEFI mode.
You also need to boot Windows repair flash drive in UEFI boot mode, so it makes UEFI type repairs.

---

