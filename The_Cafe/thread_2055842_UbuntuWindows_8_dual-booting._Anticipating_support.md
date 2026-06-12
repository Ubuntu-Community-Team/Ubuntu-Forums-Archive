---
title: "Ubuntu/Windows 8 dual-booting. Anticipating support needs."
date: 2012-09-10
forum: The Cafe
---

### Post by coffeecat on 2012-09-10
In a few weeks time, machines with Windows 8 pre-installed will become available. Windows 8 will bring with it a few new issues related to dual-booting with Ubuntu and the staff have been having a discussion about whether and how we need to anticipate these with information useful to all, especially newcomers. The issues we have identified so far, some of which have already been seen with Windows 7 but which will become commoner with the advent of Windows 8, are as follows:

[list][*]The hybrid Windows 8 hibernate/shutdown causing loss of files saved to a shared NTFS partition from another OS. See [this thread](http://ubuntuforums.org/showthread.php?t=1953674) for more.


[*]UEFI/GPT dual-booting.


[*]Secure boot. Microsoft [requires the ability to disable secure boot](http://download.microsoft.com/download/A/D/F/ADF5BEDE-C0FB-4CC0-A3E1-B38093F50BA1/windows8-hardware-cert-requirements-system.pdf) via firmware setup on non-ARM systems (page 121, #18) for hardware certification for Windows 8. In addition, [ Ubuntu 12.10 will work with secure boot enabled](http://blog.canonical.com/2012/06/22/an-update-on-ubuntu-and-secure-boot/). However, is it possible that a manufacturer could release hardware non-compliant with Microsoft's certification requirement, which would cause problems with pre-12.10 Ubuntu releases?


[*]Samba vs Windows 7/8 homegroups.


[*]Refresh and Reset functions. My own experiments with the release preview show that grub and Ubuntu survive both the Windows 8 reset and refresh functions, but this was on a conventional BIOS machine with MBR partition table. I have no UEFI machine to check this with a UEFI/GPT system.


[*]Storage Spaces.[/list]

Comments from the forum community as a whole would be valued. Specific questions are:

[list][*]Anything we've missed?


[*]Any suggestions about how we could meet this need? Is there a need? A sticky with links to wiki articles perhaps? Bear in mind that we are moving away from having full-scale howtos on the forum. Useful links would be helpful (and see next item).


[*]**UEFI booting.** The [Ubuntu wiki UEFI booting page](https://help.ubuntu.com/community/UEFIBooting) would be daunting for newcomers. Does anyone know of a guide more suited for newbies?

**EDIT** - I'd missed that the wiki page had been edited with a link to a simpler guide a little while before I posted this post. The simpler guide is [here](https://help.ubuntu.com/community/UEFI) - **endedit**[/list]

Or any other suggestions would be welcome.

Please note that this thread is not the place to discuss the pros and cons of secure boot, the pros and cons of any feature of Windows 8, your opinion of Microsoft, or anything else not related to how we provide an information resource about dual-booting with Windows 8. Off-topic posts will be removed.

---

### Post by YannBuntu on 2012-09-10
Good thread.

- UEFI is not specific to Windows8 (it has appeared with Windows7. MacUEFi may be another problem), and it is not a big problem. There are still several GRUB&Ubiquity bugs to solve, but there are reliable workarounds ( [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)). As UEFI computers are becoming numerous since 2011, I think we should add recommendations in [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) (I already updated [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) )
- Problems due to Windows8 hibernating / fast reboot. See [https://bugs.launchpad.net/wubi/+bug/1042159](https://bugs.launchpad.net/wubi/+bug/1042159) and [https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149)

---

### Post by holastickboy on 2012-10-09
I have been using Windows 8 professional as an MSDN subscriber through my university, and have successfully had both operating systems installed.  My only hint for others is that the option to "Install along side Windows" option does not work.  Users need to create a boot partition, and install the GRUB bootloader to that partition.  

EasyBCD (freeware) also allows users to add Ubuntu to their windows Bootloader (its a nice GUI that might not scare them as much as GRUB might).

---

### Post by YannBuntu on 2012-10-09
**@holastickboy:** some problems have been reported when using EasyBCD / BCDedit on a UEFI system. Have you successfully used EasyBCD on a UEFI system?

---

### Post by geo2160 on 2012-10-13
If it is of any use to you guys, I just installed ubuntu for the first time ever (dual-boot with windows 8 ). Actually, it's the first time i ever installed a linux distribution in my life. The installation went flawlessly even though i had to mess with the bcd beforehand due to an old win7 install. Dual-booting works fine and a reset of windows 8 didn't mess grub up. Considering the fact that i'm a total newb, this is fantastic work!

---

### Post by SMOKE14 on 2012-10-21
Doing a Windows 8 reset in my experience has not messed with Ubuntu.

---

### Post by searchfgold6789 on 2012-10-23
I wonder if people will ask about wubi on Windows 8, and what to tell them if they do.

---

### Post by coffeecat on 2012-10-23
> **searchfgold6789 said:**
> I wonder if people will ask about wubi on Windows 8.

Good point - thanks. I haven't seen it mentioned. Have you tested wubi in W8 yourself? If I find time, I'll see what happens when I try to install wubi in W8 in my UEFI W8/12.04 dual-boot.

---

### Post by bcbc on 2012-10-23
From what I understand, Wubi does not work in a full UEFI boot system (bug [lpbug]694242[/lpbug]). It should be okay with hybrid boot with a MBR partitioned disk.

I've been running Wubi on Windows 8 without any issues for a while. The only issue which I found from one of the bug reports identified by YannBuntu above was that if you enable hybrid-sleep then you'll have problems (but it doesn't appear as if hybrid-sleep is switched on by default). Fast-start on the other hand (which is on by default) doesn't seem to bother Wubi, but does affect a normal dual boot. I blogged about it [here]("http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html").

---

### Post by PaulInBHC on 2012-10-27
I just updated from XP Home SP3 32 bit to W8 Pro 32. Install took about an hour and everything hardware seems to work. I have an ATI HD 4200 onboard GPU.
 
When I ran the pre update check it stated that I did not have a Secure Boot drive. I installed windows on an older 7200rpm IDE drive and have 12.04 on my new SATA drive. Grub did not seem to be effected.
 
Bedtime here. Would you like me to try a WUBI install tomorrow?

---

### Post by PaulInBHC on 2012-10-29
After a few reboots bios could not read the SATA drive with 12.04 on it. Thinking that I had a bad drive I unplugged it and ran my XP disc, recovery console, fixmbr and was able to get into 8.

Could it be that EFI is preventing that drive from being read?

---

### Post by coffeecat on 2012-10-29
@PaulInBHC, this is not a technical support thread - this is for suggesting information resources for Win8/Ubuntu dual-booters. You might want to start a thread in a technical area for that.

@everyone, now that Windows 8 has been released, I'll leave this thread open for a few days for anyone who has any other useful links. Then I'll see about preparing a sticky for the Installations and Upgrades forum.

Thanks to all who have made suggestions and/or provided links.

---

### Post by Magnezone150 on 2012-10-29
Sweet, But I believe It will mostly depends on Manufacturers use for Hardware or Software.
This is Because on Youtube I use my Asus X53U-SH11-CBIL with Ubuntu 12.04 and I've recently Dual-Booted it with Windows 8 and Ubuntu's Standard Grub loader has no problem working with Windows 8 with/without Secure boot. :)

---

### Post by SMOKE14 on 2012-10-29
In my Windows 8 Pro final version, a reset in W8 does not mess with Ubuntu.

---

### Post by as2000 on 2012-10-29
Just my experience with Win8, updating grub and then using grub menu to boot into Win8, broke it. I had to do a refresh in Win8 to get it to work again. Using the bios menu (F8 on my motherboard) allowed me to boot into Win8 just fine after (I use separate drives instead of partitions).

---

### Post by YannBuntu on 2012-10-30
> **as2000 said:**
> Just my experience with Win8, updating grub and then using grub menu to boot into Win8, broke it. I had to do a refresh in Win8 to get it to work again.

This may be a bug of GRUB2. It would be useful to create a bug report here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug](https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug)

---

### Post by Eggnog on 2012-11-03
I've currently got Ubuntu 12.04 installed alongside Win 7, using EasyBCD to control booting.  My question is whether, if I decide to "upgrade" to Win 8 in the future, the upgrade process will mess with the Win MBR and crash EasyBCD's current setup.  Anyone know?

---

### Post by coffeecat on 2012-11-03
> **coffeecat said:**
> I'll leave this thread open for a few days for anyone who has any other useful links.

Thanks to all who have provided information. The thread is now closed and unstuck.

---

