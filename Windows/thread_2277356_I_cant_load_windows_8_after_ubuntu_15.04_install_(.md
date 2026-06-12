---
title: "I cant load windows 8 after ubuntu 15.04 install (boot repair link)"
date: 2015-05-08
forum: Windows
---

### Post by jonas18 on 2015-05-08
I installed ubuntu today and now i cant access my windows 8 OS.
i tried the boot repair tool but it didnt work but here is my link
[http://paste.ubuntu.com/11026358/](http://paste.ubuntu.com/11026358/)

---

### Post by jonas18 on 2015-05-08
What one weird thing is, is that there is a second grub starting with a gparted logo in the background before the normal ubuntu grub the first one i need do c /> exit out of it to get to the second one

---

### Post by oldfred on 2015-05-08
You should not normally install grub to a partition's boot sector (PBR) and never ever to a NTFS or Windows boot sector. Normally grub is just just installed to a drive or the MBR.
You have installed grub to sda3's boot sector which is your Windows. Windows has more boot code in the boot sector for its use. But it does keep a backup so if you only installed once, you can easily restore from backup with testdisk. Testdisk may say it is valid as a grub in a PBR can be valid, just that it is not correct for NTFS.

```
 sda3: __________________________________________

       File system:       [COLOR=#ff0000]ntfs[/COLOR]
    Boot sector type:  [COLOR=#ff0000]Grub2[/COLOR] (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda3 and looks at sector 950056448 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe



```

       You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]

[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by jonas18 on 2015-05-08
Hey tahnk you for the quick response 
but in mz testdisk it shows this 


Boot sector
Status: OK

Backup boot sector
Status: Bad

---

### Post by jonas18 on 2015-05-08
if i could get my hands on a windows 8 recoverz disk can i use it to recover the windows bootloader?

---

### Post by oldfred on 2015-05-08
Moved to Windows sub-forum.

If backup is bad you will need a Windows recovery console from a Windows repair flash drive or installer.

I believe it still is the same with Windows 8, but do not have a link for 8 specifically.
 How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

      
 [http://www.eightforums.com/](http://www.eightforums.com/)
[http://superuser.com/](http://superuser.com/)

More Info:
Also not sure if Windows may have issues on seeing your NTFS partition. With grub in there, it thinks it is unformatted and may give errors. If so go back to testdisk and on that recover backup screen is a create a new NTFS boot sector. That will be XP type which is different, but then Windows should see it and let you update it to Windows Vista/7/8 type boot sector.

---

