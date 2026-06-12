---
title: "Ubuntu and efi"
date: 2013-09-29
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2013-09-29
On my system I can disable secure boot, and I can use legacy/bios however with legacy/bios when I install ubuntu 13.10 or fedora 20 my windows 8 boot sector is literally destroyed and I cannot boot windows 8.

When I install ubuntu with secure boot enabled or disabled I cannot boot ubuntu either with usb or dvd.  I get error message stating that the kernel must be loaded first.

Am I missing something I thought that linux (fedora and ubuntu) could be installed with efi.

Henry

---

### Post by oldfred on 2013-09-29
Ubuntu can be installed with UEFI but not if you boot  installer in Legacy mode. How you boot install media is how it installs - UEFI with secure boot, UEFI, or Legacy/CSM/BIOS mode.

If Windows is UEFI, you should always be able to go into UEFI menu and directly boot Windows. 
Only some buggy UEFI systems will Boot-Repair rename the Windows efi file and make that name grub2's shim file that also has the Microsoft secure boot signing key. Those buggy UEFI only boot Windows and it is about the only work around other than getting vendor to fix UEFI. Then from grub menu you boot the renamed Windows efi boot loader.

Other Envy systems.
 HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

See also several links to install directions with screen examples in link in my signature.

---

### Post by Hewjr100 on 2013-09-29
For the most part those links deal with getting ubuntu to boot when installed, my issue is primarily that I cannot install at all, just get message about kernel being loaded first, then it just cycles back to grub menu ie: try ubuntu without installing or install ubuntu.

I have been trying various methods to get anything installed in a dual boot configuration.  The worst was when I enabled legacy mode and installed fedora 18 or 19.  All went fine until I rebooted.  When grub appeared, all os's were listed and fedora booted ok, but not windows 8.  I had to da a restore, so I have leaned that factory rest is and always will efi with or without secure boot.  This means obviously that the only option I have is to install linux with efi, or of course dump windows 8.

Btw I did get fedora installed with secure boot, but using f9 key then selecting fedora, then waitng for grub, then selecting fedora is kind of...well I'll be nice and say not my cup of tea .  I don't know maybe I am compulsive but for dual booting a simple grub menu at boot up is sufficient.

Now about this kernel must be loaded first, there must be a less challenging way to sort this out.  I am not interested in instructions that are more than 1 page long, and require a degree in cs.

I do enjoy using linux, but to a point.  This is why I primarily use ubuntu.  It is one of the best for linux hobbyist like myself.  Yes I know linux mint is more user friendly, but I find myself in the middle.  For example installing and customizing fedora took some time, but I did it.  On the other hand mint is like windows, change you background or or use desklets /widget like in windows 7, otherwise tinkering under the hood is verboten.

So if you can tell me how to get ubuntu installed alongside windows 8 in the first place, then I will deal with getting ubuntu and windows 8 to sing cumbaya

Henry

---

### Post by oldfred on 2013-09-29
Is this an Ultrabook with dual video and a small SSD?
What video does your system have?
Some very new systems do work better with 13.10 even though it still is beta, but will be released in Oct. If you consider 13.10 understand it may still have changes and fixes and may have issues. If issue is repeatable you should report as bug.

A few systems only install in BIOS/CSM/Legacy mode. Then you can use Boot-Repair to convert from BIOS to UEFI.

---

### Post by Hewjr100 on 2013-09-29
Good.  But will boot repair actually fix windows 8 corrupt boot sector?  This is what happened a couple of weeks ago with fedora, not 20 I believe it was f19.  When I tried my recovery media, with repair option, it failed to fix boot sector, hence I reinstalled.  Trust me I don not like restoring oem image, this pos takes no les than 3 hours to finish.

Nope simple notebook with dual core i5 intel 3rd generation and intel hd 4000 graphics.  I can install just about any linux distro, as a stand alone os.

Henry

Ps I have reccent, by hp standards bios.  As you know I can't use bioses from bios manufacturer.

---

### Post by oldfred on 2013-09-29
Usually with Windows, you run chkdsk maybe more than once and that fixes PBR - partition boot sector.

You may need a Windows 8 repair flash drive as you cannot always get to repair console with f8.
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

