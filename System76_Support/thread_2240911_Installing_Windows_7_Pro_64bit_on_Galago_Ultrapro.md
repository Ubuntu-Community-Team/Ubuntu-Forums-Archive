---
title: "Installing Windows 7 Pro 64bit on Galago Ultrapro"
date: 2014-08-23
forum: System76 Support
---

### Post by ubducted on 2014-08-23
I initially had difficulty trying to install Windows 7 Pro 64bit on my new Galago Ultrapro.  Thought I'd share my experience here.

The laptop was ordered with an mSata drive then I installed my own SSD.  On a side note, installing an SSD in this laptop is super easy.

The mSata is is on sdb (the "second" hard drive) while the new SSD was on sda (the "first" hard drive).  I thought this would be perfect because MS windows always seems to want to be on the first drive in order to install.  

After installing the drive, I booted into Ubuntu and formated the new SSD as NTFS and set the "boot" flag.  I used an external CD drive for my Windows 7 disk and booted into that going through these steps: [http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine) 

Selecting the new SSD and trying to install resulted in an error: "[FONT=arial][SIZE=2]Setup was unable to create a new system partition or locate an existing system partition[/SIZE][/FONT]"

There is no UEFI stuff in my case.  The only way forward was to make the mSata (where ubuntu was installed) empty.  That is, I deleted both partitions so that it was unallocated.  After that Windows installs fine.  It's annoying to have to reinstall Linux, but at least the bootloader will find the Windows install without rebuilding Grub which was my original plan.

Some helpful forum posts I found along the way:
[http://ubuntuforums.org/showthread.php?t=1967664&highlight=Unable+to+create%2Flocate+system+partition](http://ubuntuforums.org/showthread.php?t=1967664&highlight=Unable+to+create%2Flocate+system+partition)
[http://ubuntuforums.org/showthread.php?t=2147421&page=2&highlight=Unable+to+create%2Flocate+system+partition](http://ubuntuforums.org/showthread.php?t=2147421&page=2&highlight=Unable+to+create%2Flocate+system+partition)
[http://knowledge76.com/index.php/Windows_-_Dual_Boot_Windows_On_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Dual_Boot_Windows_On_Your_System76_Machine)

This one was also interesting but I'm glad I didn't have to do it: [http://druss.pp.ua/2014/07/fixed-setup-was-unable-to-create-a-new-system-partition-or-locate-an-existing-system-partition-during-installing-windows-8-18-7-vista-etc-from-usb/](http://druss.pp.ua/2014/07/fixed-setup-was-unable-to-create-a-new-system-partition-or-locate-an-existing-system-partition-during-installing-windows-8-18-7-vista-etc-from-usb/)

Perhaps it's just their can't be other bootable drives on the system when installing Windows?  Seems to still be the rule of thumb since Windows 95.

---

### Post by ubducted on 2014-08-24
Just an additional note.  When you have to disks like I do, keep in mind the boot priority.  For me it was set to the mSata.  When I put Linux on the disk that was not set to boot first in the BIOS, the linux bootloader defaulted to the mSata device.  This overwrites the Windows bootloader and made my windows unbootable for some reason.  It was easy enough to repair that with the windows disk, then reinstall grub but on the "linux" disk.

BTW, someone told me the "boot" flag is irrelevant for Linux.  It's more a Windows thing.

Although there was a couple hiccups dual booting this Galago Ultrapro, it works well once it's up and running.  The only issue now is getting the drivers installed on Windows.  Linux installs flawlessly with the hardware, but Windows feels like I'm back in the 1990's.  Nothing works "out of the box".  

Note that a USB stick will not connect on a fresh install of Windows7.  I had to put the files on a CD and use an external USB CD drive.  How ridiculous is that...  The only other way I could think to get access to the files would be directly from the site through a wired internet connection.  But that's dangerous if you don't first have antivirus installed.

---

### Post by oldfred on 2014-08-24
If you still had BIOS set to boot from mSATA drive when installing Windows to SSD, then that was the issue. 
Windows wants to put its boot files on the drive set as boot. Usually that is the sda or first drive and not an issue.

Window in BIOS mode does require a primary partition formatted NTFS with the boot flag. Or unallocated space. Default install will use two partiions, one the boot partition that it wants to put on BIOS boot drive and main install, but if partition is created in advance it will install to one partition.

Grub does not use boot flag in BIOS, Windows & the old Lilo boot loader use the boot flag to know which partition has more boot files. But a few BIOS require a boot flag so even if just Linux we suggest a boot flag on a primary partition.

In UEFI the gpt partition with the boot flag is the partition where all systems put boot files. It is not like a boot flag in BIOS and seems to only be a parted tools convention. Gdisk uses ef00 to indicate the efi or ESP partition. And it actually is a very long GUID code.

---

