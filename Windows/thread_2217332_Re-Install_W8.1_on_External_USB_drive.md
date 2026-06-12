---
title: "Re-Install W8.1 on External USB drive?"
date: 2014-04-16
forum: Windows
---

### Post by NTL2009 on 2014-04-16
I realize this is really more of a Windows question, but searching the web brings up so many unrelated topics (installing Windows from USB) that I couldn't find what I wanted.


My situation is that I have a new laptop arriving soon (Lenovo G710) with W8.1. I almost never use Windows, but I'd kinda like to keep a bootable version around, just in case. But I really don't want it taking up room on my internal drive.

So can I:
 [INDENT]
A) Make W8.1 restore disks if none are included, then 
B) Wipe the internal HDD, 
C) Install Linux to the internal HDD (probably Xubuntu 14.04 in a few days)

and then

D) Use the Restore disks to install a bootable W8.1 on an_ external USB HDD_? And boot from that if/when I want?
[/INDENT]


That would be great. I'd have Win 8.1 just in case, and still have my full internal HDD available to me.

TIA for any help - NTL2009

---

### Post by slickymaster on 2014-04-16
Moved to Other OS/Distro Support.

---

### Post by Mark Phelps on 2014-04-17
Except for the Enterprise editions, Windows 8 does not INSTALL to an external drive.  The version that does is known as WindowsToGo and is only the Enterprise edition.

---

### Post by NTL2009 on 2014-04-17
Thanks Mark Phelps. I saw references to that Enterprise Edition and the WTG, but wasn't sure about the details.

So I'll go to an alternate plan - I have an older, working 250GB drive from upgrading my current laptop a few years ago. I'll wipe that, temporarily swap it on my new machine, install W8.1 from the restore discs, check it out, and then remove it and wipe/install Xubuntu on the HDD that comes with my new Lenovo. 

That means I'll need to physically swap out drives to boot W8.1, but I don't think I've even tried it more than one or two times in over three years on my current machine, so that is preferable to giving up my disc space for it.


-NTL2009

---

### Post by oldfred on 2014-04-17
If it is a new system you need to pay attention to whether you boot installer for both Windows & Ubuntu in UEFI or BIOS mode. How you boot install media is how it installs.
Always best to have both systems in same mode either both UEFI or both BIOS.
And whether you really want BIOS/MBR partitioning or UEFI/gpt partitioning.
With Ubuntu you also can have gpt partitioning with BIOS boot, but then Windows will only install to gpt partitioned drives with UEFI.

I now suggest gpt partitioning for any drive that will not be Windows ever whether you want UEFI or BIOS. As then you can convert later if  you want to. But then you also should leave space or create an 300MB FAT32 efi partition with the boot flag at beginning of drive. And if BIOS booting you need a unformatted 1 or 2MB with the bios_grub flag.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by NTL2009 on 2014-04-17
Thanks oldfred.

This is my first install on a UEFI based machine, so I do have some reading to do. I'll bookmark those links.

Fortunately, I can take my time. I'm going to stay on my current EM725 with Xubuntu 12.04 as my 'everyday' machine, and I won't switch over to the new G710 until it is all configured the way I want. I can just rsync my 'documents' folder, which is all cleaned up pretty well so I can keep the same organization. So a few mistakes along the way (aka 'learning' ;) ), even if I have to wipe and start over a few times won't really be very painful.

Then my EM725 will be freed up for all sorts of 'fun' experiments. It'll be nice to be able to try out different variants w/o risking and interrupting tasks on my 'everyday' machine, maybe play with MythTV/Mythbuntu.

-NTL2009

---

