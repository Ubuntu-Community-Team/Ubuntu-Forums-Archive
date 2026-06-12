---
title: "Ubuntu server installation hangs at grub-install dummy"
date: 2018-06-26
forum: Server Platforms
---

### Post by vatharian on 2018-06-26
Hello!

I'm attempting to install Ubuntu server on my system, and it fails every time.
I've tried installs using Ubuntu 16.04 LTS, 17.10, and 18.04 LTS (alt installer) ISOs, all hang in same spot (grub-install dummy, 50%)

Hardware: Intel S5520HC (dual Xeon X5570, 48GB ECC-R memory), newest BIOS (march 2018), EFI mode (required because of Raid cards that will be added later), single SATA SSD.

So far my workaround for systems with problems installing OS has been to pull out the disk, drop it into Virtualbox VM with raw media access, and install OS there. This time however, when running apt upgrade on target board system completely hangs when installing new kernel, probably - when reinstalling grub, leaving me with the grub's bash-like command line and no way to boot the system.

Same computer works (and installs) fine under Windows 10.

What steps should I take to troubleshoot this problem?

---

### Post by oldfred on 2018-06-27
Moved to server sub-forum.

I do not know server, but some have posted issues with new server gui installer. It works, but only for some cases.
See new server section
[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes#Ubuntu_Server](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes#Ubuntu_Server)

UEFI version must be booted in UEFI mode and if you partition in advance, you must have an ESP - efi system partition. (FAT32 with boot flag) or if using gdisk code ef00.

What brand motherboard. I know desktop versions of some brands need boot kernel parameters.
And many UEFI require various settings. If you updated UEFI, it reverted many settings to defaults, so check those.

If you also have Ubuntu live Desktop, you can run this. It requires a gui to work so cannot run from server installer.
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If no gui, you can run this, which is used as first part of Boot-Repair's summary report:
       
 Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

---

