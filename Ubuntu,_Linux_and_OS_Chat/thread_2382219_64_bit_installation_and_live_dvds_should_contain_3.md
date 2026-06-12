---
title: "64 bit installation and live dvds should contain 32 bit efi files"
date: 2018-01-10
forum: Ubuntu, Linux and OS Chat
---

### Post by raphaell2 on 2018-01-10
There are some laptops that have 64 bit chips, but come with 32 bit uefis and 32 bit Windows versions preinstalled. Right now, it seems to be impossible to install any version of Ubuntu on such laptops, or even get the dvds to boot, because regular 64 bit dvds aren't recognized as proper bootable mediums by the uefis of such laptops, while 32 bit dvds and modified 64 bit dvds aren't recognized as any kind of bootable mediums (and yes, I tried disabling safe boot, fast boot, quiet boot, etc.). It would by great if in future Ubuntu versions, 32 bit efi files would be included on the 64 bit dvds (they'd take up very little space), so that people could use Ubuntu on such laptops.

---

### Post by TheFu on 2018-01-11
Nobody from Canonical comes here.  If you want them to see it, open a bug on launchpad.

However, many Linux distros are dropping 32-bit support, so I wouldn't expect much effort on this issue.  Heck, even my purpose-built router is running a 64-bit AMD CPU.

Are these old Windows laptops running a supported OS (Win7+)???  Do they support legacy BIOS boot?  32-bit Linux distros will probably support that without issues.

---

### Post by oldfred on 2018-01-11
Most of the 32 bit UEFI systems are the very lightweight (low cost) tablet or laptops still with Windows 10.
When they first came out Linux did not have the 32 bit UEFI, so Microsoft & the vendors thought they had locked users into Windows similar to Apple.

Back in 2013 this was discussed.
 32-bit UEFI Support Proposed For Ubuntu Linux bootia32.efi
[http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE](http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE) 

 Don't ship 32-bit UEFI firmware on x86
[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)
Some new 64 bit low cost systems with 32 bit UEFI
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855) 

I did not think it was now that difficult to copy bootia32.efi into Ubuntu's flash drive and have it boot a 32 bit system. May require some changes to grub.
But have not done it.
Many of these lightweight system also need multiple or different boot parameters and some effort to configure as not really standard PC.

---

### Post by raphaell2 on 2018-01-11
Yes, the laptop I'm talking about is a bit over a year old - not that old. I have, now, managed to copy bootia32.efi into the right place on a flash medium - it was a bit complicated, because normally bootable flash drives are absolutely configured to be mounted read-only, in a way that can't even be overturned with sudo. But now it only boots into a shell, with apparently no way to install anything.

---

### Post by oldfred on 2018-01-12
This would probably be the better way to create the flash drive.
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 

Then you just need to add /EFI/Boot/bootia32.efi. Some posts depending on model of system also required edits to grub to may it work.

---

### Post by qyot27 on 2018-01-12
> **TheFu said:**
> Nobody from Canonical comes here.  If you want them to see it, open a bug on launchpad.

However, many Linux distros are dropping 32-bit support, so I wouldn't expect much effort on this issue.  Heck, even my purpose-built router is running a 64-bit AMD CPU.

Are these old Windows laptops running a supported OS (Win7+)???  Do they support legacy BIOS boot?  32-bit Linux distros will probably support that without issues.
Well, the setups in question aren't 32-bit; they have 64-bit processors (typically a Silvermont or one of its successors).  Just the UEFI firmware is 32-bit.  But since the Linux kernel has supported UEFI mixed-mode for several years, it's fully possible to install 64-bit Ubuntu on them and use the full capabilities of the CPU.

The rationale for it is usually quoted as being because they ship with Windows, and putting 64-bit Windows 8 (when they first started appearing a few years ago) or 10 on there would take up too much storage space, and these ultra-low-power setups often only have 32GB eMMC main storage.  So because Windows has to match the UEFI firmware bittage, and they're using 32-bit Windows for space reasons, they have to use 32-bit UEFI.  And there is no Legacy BIOS fallback in these things - it's UEFI-only.

I'm familiar with it because I have a Quantum Byte, a mini-PC that's part of this group.  I don't actually have Ubuntu installed to the internal storage, I did a full install to a 128GB USB drive and run it from there.  Copying bootia32.efi into a Live USB is pretty much the only option to get any install media to boot, unless you want to re-spin a LiveCD with bootia32.efi included and hope it works, and then they can be pretty finicky about getting the partitions on an external drive set up correctly to boot from there instead (including having to use the GRUB2 shell to manually boot once it is installed).  Debian supports UEFI mixed-mode Live/Install media, FWIW, but bootia32.efi often needs to be specifically tailored to the SoC in question or else it won't work.

Even getting a 32-bit Linux distro installed requires them to have bootia32.efi because the firmware doesn't have Legacy BIOS mode.  Finding UEFI-enabled 32-bit media is probably even more rare than just copying bootia32.efi into a 64-bit Live USB.

---

