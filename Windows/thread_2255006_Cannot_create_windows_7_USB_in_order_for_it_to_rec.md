---
title: "Cannot create windows 7 USB in order for it to recognize my 4TB drive"
date: 2014-12-01
forum: Windows
---

### Post by hakermania on 2014-12-01
So, the last few hours I'm trying to solve this...

I want to dual boot a 4TB hard drive.

I know that it is easier to install Win7 and then Ubuntu, so I boot into my Live Ubuntu USB, a make a GPT partition table (in order to support those 4TBs) and then I attempt to install from the Win7 USB (which I've created by extracting the ISO from the CD and then burning it to the USB using WinUSB (a tool available for Linux)).

The thing is that Win7 installs in just the 2TB drive and seems to revert the partition table to MBR (from GPT). If, after the Win7 installation to the 2TB, I attempt to install Ubuntu to the remaining 2TB, I am getting an error saying that this isn't a GPT table etc. This shows me that Win7, during the installation have reverted the partition table type.

I've read various sources for solving the issue. Some of those indicate that I should just boot my Win7 media (either CD or USB) through UEFI and not Legacy. In order to boot my USB through UEFI it needs to be formatted to FAT32 while WinUSB creates NTFS image. Somebody said to let WinUSB do its job, copy the files from USB to hard drive, format USB to FAT32, pass files back to USB. This didn't work; while booting from that USB I was finally placed on a grub console (that was really weird, I thought I installed windows into the USB? What is WinUSB exactly doing?).


Does anyone have any ideas on how to make this work? Should the first step be booting from the Live Ubuntu USB and setting the partition table to GPT?

---

