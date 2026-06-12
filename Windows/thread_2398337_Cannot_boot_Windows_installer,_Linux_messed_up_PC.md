---
title: "Cannot boot Windows installer, Linux messed up PC"
date: 2018-08-10
forum: Windows
---

### Post by greenfork+ on 2018-08-10
Hi,

So I recently installed lubuntu, because I wanted to try it out and I really liked it. However I wanted to return to windows. But I cannot do that, since when I put in the CD or a USB (Doesn&#7831; matter which one) it comes up a black screen when booting up saying "Reboot and Select proper Boot device or innsert  Boot Media in selected boot device and press a key" It only accepts the USB if it got linux installation on it, but not windows.

I installed linux on the whole hard drive, so there is no dual boot. It installed something called Grub as well. Not sure if that got anything to do with it.

Any idea why?

---

### Post by oldfred on 2018-08-10
Moved to Windows sub-forum since Windows issue.

That would be only if you do not have a properly configured Windows installer.
Or you are booting in wrong boot mode, UEFI or BIOS if newer hardware.

But it should whether UEFI or BIOS change to second device in boot order and then just boot grub boot loader and your Lubuntu install.

Also version of Windows can make a difference. All hardware in last 5 years or since Windows 8 released is newer UEFI hardware. Both Windows 8 & 10 can install in either UEFI with gpt partitioning or BIOS with MBR partitioning.
Windows 7 installer defaults to BIOS only, but can be reconfigured to boot in UEFI mode from flash drive if files moved & renamed. But if you try to boot BIOS version in UEFI mode, it will not work unless converted.

---

### Post by greenfork+ on 2018-08-11
Hello,

Thank you for your response. The windows installer has worked before I installed ubuntu and works to any other computer, but not on this PC.

I am trying to boot with windows XP at the moment, but also tried windows 7 and 10. I put the USB first in the boot order aswell. The PC is rather old.

I also tried to format the hard drive in order to remove linux, but still wont boot from USB or CD :/

---

### Post by oldfred on 2018-08-11
My older BIOS only system booted USB flash drive as another hard drive, not any of the USB boot options.

---

### Post by greenfork+ on 2018-08-14
The weird thing is that it wont even boot from the CD. This is driving me crazy, I tried to format the HDD as well, so right now there is no linux installed.

---

