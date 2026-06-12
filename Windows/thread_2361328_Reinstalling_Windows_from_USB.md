---
title: "Reinstalling Windows from USB"
date: 2017-05-15
forum: Windows
---

### Post by sneakypotato180 on 2017-05-15
Hello,

I am new to the Ubuntu OS, I am having some issues with installing windows back onto the drive. I have a Windows install on a USB stick. The image works as I have used it before. But when I attempt to use it on this Ubuntu setup it comes up with the following error

Failed to open \EFI\MICROSOFT\BOOT\grubx64.efi - Not Found

I have installed Ubuntu on a laptop that came with Windows pre-installed. Could this be causing the issue? I have been on many other threads and nothing has helped so far. I am brand new to Ubuntu so I don't know much about the Terminal and so on.

I have ran Boot Repair but nothing really changed. Anyone know what I should do I am a little lost.

---

### Post by oldfred on 2017-05-15
Moved to Windows sub-forum.

This file should not exist:
\EFI\MICROSOFT\BOOT\grubx64.efi

Your grubx64.efi is supposed to be in /EFI/ubuntu and can be in /EFI/Boot, but not in the Microsoft folder.

And the external flash drive only boots from /EFI/Boot/bootx64.efi. And that file with Windows is a Windows UEFI boot files or with Ubuntu it is a grub/shim UEFI boot file. UEFI requires that name for external devices.

Make sure you are booting in UEFI boot mode, as Windows installs in same mode as your boot installer, just like Ubuntu does. 

 May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by sneakypotato180 on 2017-05-18
> **oldfred said:**
> Moved to Windows sub-forum.

This file should not exist:
\EFI\MICROSOFT\BOOT\grubx64.efi

Your grubx64.efi is supposed to be in /EFI/ubuntu and can be in /EFI/Boot, but not in the Microsoft folder.

And the external flash drive only boots from /EFI/Boot/bootx64.efi. And that file with Windows is a Windows UEFI boot files or with Ubuntu it is a grub/shim UEFI boot file. UEFI requires that name for external devices.

Make sure you are booting in UEFI boot mode, as Windows installs in same mode as your boot installer, just like Ubuntu does. 

 May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Thank you, I will try that out.

---

