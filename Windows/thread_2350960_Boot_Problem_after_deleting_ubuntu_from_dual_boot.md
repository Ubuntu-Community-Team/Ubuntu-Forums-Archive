---
title: "Boot Problem after deleting ubuntu from dual boot"
date: 2017-01-29
forum: Windows
---

### Post by rainbowzom on 2017-01-29
Recently, I deleted ubuntu from my windows 10 and ubuntu dual boot, in order to save some space.
I booted up windows fine, but after a forced shutdown, it showed "grub rescue, no such partition".
So naturally I looked online and found something called "boot repair", copied it to my usb, and booted up my laptop.
After repairing the mbr, I rebooted my laptop. I change the boot order back to hdd. However, all it shows now is a blinking cursor. 
I really would like to keep my files. And yes, I know it was stupid of me to not backup.
Any help would be appreciated. Thanks so much :)

---

### Post by howefield on 2017-01-29
Thread moved to the "*Windows*" forum.

---

### Post by yancek on 2017-01-29
Boot repair has an option to Create BootInfo Summary which you need to select and post a link to it.  Without that, there is nothing anyone here can do to help, no useful information.

---

### Post by oldfred on 2017-01-29
UEFI or BIOS?
Forced shutdown often damages file system. With Windows then you need chkdsk. With Linux you run fsck.

You probably need your Windows repair disk or installer with the repair console.

You did make this as soon as you got system?
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html) 

You cannot run chkdsk from Linux, but some third party Windows repair tools may include it.

 Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required
chkdsk c: /b
/b includes /r
[URL="http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx"]http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx

[/URL] Windows 10 chkdsk
[https://www.tenforums.com/tutorials/40734-drive-error-checking-windows-10-a.html](https://www.tenforums.com/tutorials/40734-drive-error-checking-windows-10-a.html) 

[URL="http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx"]
[/URL]

---

### Post by rainbowzom on 2017-01-29
BIOS with legacy mode. 
Heres my log
[http://paste.ubuntu.com/23888656/](http://paste.ubuntu.com/23888656/)

Im currently downloading windows 10 usb from my other computer

---

### Post by oldfred on 2017-01-29
```
sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda2 and looks at sector 1435882144 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
```

You almost never install grub to a partition, and you never ever install to a NTFS partition as that breaks Windows.
Windows has essential boot info in the Partition Boot Sector (PBR or BS).
But NTFS keeps a backup and you normally can use testdisk to restore the backup.

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

### Post by rainbowzom on 2017-01-29
Sorry, Im really a novice. Is it possible that you could provide me with step by step instructions? If not its fine as I'll try to follow the links

---

### Post by oldfred on 2017-01-29
Best to review links, so you have some idea of what you are doing.

But the testdisk site is a step by step set of instructions and the part you really want is near bottom. NTFS partition recovery.

---

### Post by rainbowzom on 2017-01-29
I went into testdisk and it says 'ok' for boot sector and backup boot sector for both of the partitions.
also,when using analyze, i cannot find any partition callwd 'partition 3'
Futhermore, is the boot partition the smaller one?

---

### Post by oldfred on 2017-01-29
Yours is sda2, example was using sda3.

Grub in a partition can be valid, just never valid in NTFS.
So you want to restore the backup. 

You normally have boot flag on sda1, and it then is a Windows boot partition.
You are missing the /boot/BCD in sda2, so it would not boot even after you fix PBR/BS. 
So also move boot flag with gparted or using your Windows repair disk and set active command.

---

### Post by rainbowzom on 2017-01-29
Im not quite sure what Im supposed to do in testdisk then... Everything looks fine inside of testdisk. Im also quite new to gparted.
When I check the flags in gparted, it says that boot is a flag in sda2. What does that mean?
Again, Im sorry as Im quite tech illiterate

---

### Post by oldfred on 2017-01-29
Windows adds a boot flag to the partition which has more boot files/settings.
The partition with the boot flag then is where bootmgr & BCD should be.

So you want in gparted to remove boot flag from sda2 and move it to sda1.

And in testdisk you need to restore the backup BS for sda2 even though it may say BS is valid. It just does not know that grub is not invalid in the NTFS formatted partitions. Grub can be valid in a PBR/BS, but almost never should be in the PBR.

---

### Post by rainbowzom on 2017-01-29
By restore the backup, you mean, "rebuild BS". Also, is sda2  the one with the larger number in "size in sectors"?
I tried doing rebuild BS on sda2, and it returns with "Extrapolated boot sector and current boot sector are identical"

---

### Post by oldfred on 2017-01-30
No, not the rebuild BS as that is only if the restore the backup does not work.

And if you run the rebuild BS, I believe that still creates the XP type BS, and to convert to newer Windows Vista, 7, 8, or 10 type you have to run chkdsk from your version of Windows using your Windows repair disk.

If grub is still in the PBR/BS then Windows will not even see sda2 is NTFS and will not run chkdsk at all. That is why you must restore from backup if possible as that then is the newer version also. 

If it did run the rebuild BS, then grub may now be the back up and you have lost the original correct BS.
Then your only choice is to verify what is in PBR by re-running summary report from Boot-Repair and if Windows XP type, then run chkdsk using Windows repair console.

You may be able to then use Windows repair console  and BootRec.exe /FixBoot      command or this:
       Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

