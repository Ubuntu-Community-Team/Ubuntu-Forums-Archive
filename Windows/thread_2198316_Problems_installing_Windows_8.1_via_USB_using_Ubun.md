---
title: "Problems installing Windows 8.1 via USB using Ubuntu v12.04 LTS"
date: 2014-01-08
forum: Windows
---

### Post by jake-allen-a on 2014-01-08
I'm trying to install Windows 8.1 via Flash Drive, currently using Ubuntu. [B]

Notes; [/B]
* The ISO file is mounted to a 16GB hard-drive formatted with FAT32. I used GPart Partition to do this.  
* It is flagged as a bootable device in Disk Utility and GPart, and is the top on my boot settings in my BIOS 
* I am NOT trying to make this dual-boot, or make this a bootable  Windows flash drive, just trying to install Windows via the Flash Drive  itself - that's all - format over Ubuntu 
* The Autorun.inf, as well as the Bootmgr file are present on the flash drive 
 * Ubuntu version 12.04 LTS

**The Problem:  **
Upon booting from it it immediately brings me to the error screen  saying, "*this is not a bootable disk. please insert a bootable floppy*" 

Research/Googling only led to results saying the hard-drive crashed but this is not the case. It's booting the flash drive obviously, just failing. Which before I get asked, yes it is functional - which should be obvious since I've gotten to this point. Lol.

---

### Post by oldfred on 2014-01-08
Moved to other OS since Windows issue.

You may get better help here:
       [http://www.eightforums.com/](http://www.eightforums.com/)

Did you extract ISO? And install boot loader to drive? Boot flag does not install boot loaders, but just says which partition has Windows boot files.

I doubt that Windows is different from Ubuntu in that you do not normally directly boot an ISO. 
Grub can loopmount Ubuntu ISO, but it is configured for that.

---

### Post by jake-allen-a on 2014-01-08
> **oldfred said:**
> Moved to other OS since Windows issue.

You may get better help here:
       [http://www.eightforums.com/](http://www.eightforums.com/)

Did you extract ISO? And install boot loader to drive? Boot flag does not install boot loaders, but just says which partition has Windows boot files.

I doubt that Windows is different from Ubuntu in that you do not normally directly boot an ISO. 
Grub can loopmount Ubuntu ISO, but it is configured for that.

Ahh, thank you. I tried to find the right forum but I'm not very familar with the layout here obviously. 

The ISO is extracted, but you might be onto something with the boot loader. I think it's just flagged and that's it. What would I use to do that?

---

### Post by oldfred on 2014-01-08
If you install ISO with the tools, and I do not know Windows tools anymore, it should make it bootable.
Windows had boot code both in MBR and in PBR or partition boot sector. Usually the PBR calls out ntldr for XP or bootmgr for all the newer versions.
Not sure on installer as that is FAT32 which is somewhat different than the NTFS PBR.

Is your system UEFI? 
[http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html](http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html)

---

### Post by mips on 2014-01-09
Use the windows USB installer tools for this.

---

