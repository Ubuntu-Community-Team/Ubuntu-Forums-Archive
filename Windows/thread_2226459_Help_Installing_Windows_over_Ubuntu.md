---
title: "Help Installing Windows over Ubuntu"
date: 2014-05-27
forum: Windows
---

### Post by aflow01 on 2014-05-27
Hey Guys, 
    Kind of a novice, love ubuntu, but have decided to just have ubuntu on one of my two computers and not both.  I think I may have messed up.  I had Ubuntu on my desktop, and I wanted to reinstall windows.  So I basically created a bootable windows disk to install, I booted into it, and then clicked "custom installation" where I then deleted the ubuntu partition (thinking that I would be able to just install windows on the space once the ubuntu partition was delete).  I now cant seem to do anything.  I cant install windows on the partition I get, "Windows cannot be installed to this disk, the selected disk is of GPT partition style".  I cant click "Repair your computer" I get, "this version of system recovery options is not compaitble with the version of windows you are trying to repair".

If I just let the computer boot without booting into the windows usb I get taken to a GNU Grub screen.

Any help would be appreciated, im totally stuck.

---

### Post by oldfred on 2014-05-27
Moved to OtherOS since Windows.
What version of Windows?
What computer. BIOS or UEFI?
If drive is gpt partitioned then Windows will only install in UEFI boot mode and you have to boot Windows installer in UEFI mode.
Or you have to convert back to MBR(msdos) for Windows to boot in BIOS mode, if new UEFI it really is CSM mode.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 


 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

---

### Post by aflow01 on 2014-05-27
Hi there, 
    Sorry just trying to understand why you responded with.  I can confirm that the drive is gpt partitioned, so from what you are saying, I have to boot my usb windows installer in "UEFI" mode?  How do I go about doing that?

---

### Post by oldfred on 2014-05-27
Is your system UEFI?
Ubuntu will install with gpt partitioning and boot in either BIOS or UEFI. 
My systems is partially from 2006 & 2009, and I use gpt but boot with BIOS. I have no UEFI capability.

If you system is UEFI, it should show two boot options.
But it depends on what version of Windows you are installing. 
XP does not work with UEFI nor gpt. 
Windows 7 has to be converted to USB and some minor updates, as DVD is BIOS only. 
Windows 8 should give both choices.

If you system is not UEFI, you need to convert from gpt to MBR. A full reformat will do that.

Do not know all the details on Windows, as my last install was XP in 2006 and I shut it down several years ago.

---

