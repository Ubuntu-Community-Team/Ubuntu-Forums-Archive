---
title: "Windows MBR destroyed in multi-boot system"
date: 2021-01-24
forum: Windows
---

### Post by olddevjohn on 2021-01-24
Hi,
I have been running a multi-boot PC with Win-7 and Mint (20.1).  I was trying to improve the boot process by using EasyBCD which I had previously used to configure the boot process.  The result was that Linux boots fine via Grub, but WIN-7 does not boot.  Trying to reconfigure the Gub menu does not work, but WIN-7 and Windows recovery are listed by the Grub menu, but one crashes the system, the other returns to the Grub menu.  I have tried using Boot Repair, both the standard repair option and also the replace MBR option in the advanced section.  Neither make any visible change to the bootsequence.  I originally installed WIN-7 using a copy of WIN-7 on a memory stick with USB drivers slipsttreamed in to overcome the problem of installation on modern hardware.  I no longer have that memory stick, so don't have a system image to try a repair from.  Any help or comment would be appreciated.
The Boot Repair info file is contained in a pastebin with the following URL
[http://paste.ubuntu.com/p/pR8D6kshTY](http://paste.ubuntu.com/p/pR8D6kshTY)

Many thanks,  John

---

### Post by oldfred on 2021-01-24
You almost never install grub to a partition, and never install grub to a NTFS partition as that breaks Windows.
Windows has essential boot info in the PBR or BS - partition boot sector which is like MBR, but for a partition.
NTFS does have a backup, which you need to see if you can restore from that.

```
nvme0n1p1: __________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       nvme0n1p1 and looks at sector 342308280 of the same 
                       hard drive for core.img, but core.img can not be found 
                       at this location. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /grldr /bootmgr /Boot/BCD /grldr
```

Many Windows tools also do a repair.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

You may also need chkdsk which you can only run from your Windows repair/recovery or Windows installer's repair console.

Best not to even run Windows 7, it is EoL - end of life and you not only present a hazard to yourself but also the rest of us. If a hacker takes over your system, it can spam the entire Internet.

Also since newer UEFI hardware, better to use UEFI installs of newer Windows & Ubuntu.
Microsoft has required vendors to install in UEFI mode to gpt partitioned drives since release of Windows 8 in 2012.

---

### Post by DuckHook on 2021-01-24
*Thread moved to **Windows** as the more appropriate forum.*

---

