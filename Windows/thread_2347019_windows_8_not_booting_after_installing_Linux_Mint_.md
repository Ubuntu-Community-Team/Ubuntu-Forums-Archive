---
title: "windows 8 not booting after installing Linux Mint 18.1 Cinnamon x64"
date: 2016-12-20
forum: Windows
---

### Post by sasha42 on 2016-12-20
Hello! 
I have installed my first Linux today (Linux Mint 18.1 “Serena” Cinnamon). At the same time I wanted to keep my old windows 8. Linux is running great and I love it. Unfortunately, windows won't boot anymore. I can choose it the grub menu, then it switches to a black screen with an intermittent underscore in the upper left corner and nothing more; I need to restart the computer to boot into linux again.  
Here is the log from the boot-repair: [http://paste2.org/LYUp4MHE](http://paste2.org/LYUp4MHE)

Thank you!

---

### Post by howefield on 2016-12-20
Thread moved to the "*Windows*" forum.

---

### Post by oldfred on 2016-12-20
You have installed grub to the PBR or partition boot sector of Windows. Windows has essential boot info in NTFS PBR, so it then cannot boot. NTFS does keep a backup, so you may be able to just restore from backup boot sector. Testdisk may say grub is valid in the BS, but it cannot be valid in a NTFS partition and is not normally installed to any partition, just MBR.

      ```
 sda1: ________________________________

 File system:       ntfs
Boot sector type:  Grub2 (v1.99-2.00)
Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of  
     sda1 and looks at sector 1507472976 of the same hard 
   drive for core.img, but core.img can not be found at 
   this location. No errors found in the Boot Parameter 
   Block. 
  Operating System:   
 Boot files: /bootmgr /Boot/BCD /Windows/System32/winload.exe 
```

 PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section on NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]

---

### Post by sasha42 on 2016-12-21
it worked. thank you very much, oldfred!

---

