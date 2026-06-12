---
title: "Grub and update-grub can't find Windows"
date: 2018-11-04
forum: Ubuntu Development Version
---

### Post by szm1gluu on 2018-11-04
Hi. I tried like everything (boot repair, partition mount, etc.)
Grub can't find my windows partition
I have 2 of windows on 1 disk, 1 from pc and another one from laptop (and ubuntu)
here's pastebin link from boot repair
[http://paste.ubuntu.com/p/yG4Tqz6C7S/](http://paste.ubuntu.com/p/yG4Tqz6C7S/)

---

### Post by oldfred on 2018-11-04
Several Windows issues, so grub cannot find it.

Windows uses boot flag to find primary NTFS partition with boot files. Grub looks for actual files.
It looks like you must have deleted the Windows Boot partition. You are not showing bootmgr & BCD anywhere.
       Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe  

You do not have to have separate Windows Boot partition, but must have all three files in a primary NTFS partition with boot flag.
That cannot be repaired from Linux, you need Windows repair console from Installer or repair disk. Maybe some third party tools.

But you also installed grub to the NTFS partition. You almost never install grub to a partition like sda4, only to a drive like sda.
And you never, ever install grub to a NTFS partition. NTFS has essential boot info in its PBR/BS boot sector. But NTFS has  a backup that you normally can restore.
      
 Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

