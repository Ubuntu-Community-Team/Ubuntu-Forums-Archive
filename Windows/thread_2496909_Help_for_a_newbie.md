---
title: "Help for a newbie"
date: 2024-04-16
forum: Windows
---

### Post by maxxon64 on 2024-04-16
Hi all, this is my very first time in this forum, i hope I am posting in the right place.
Maybe someone can help me with my PC win 10 whichafter a mains problem did not reboot anymore.
I have run PC repair but I have difficulties in understanding the log....maybe someone can help me:
```
boot-repair-4ppa2074                                              [20230320_1438]


============================== Boot Info Summary ===============================


 => Windows is installed in the MBR of /dev/sda.


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /boot/BCD


sda2: __________________________________________________________________________


    File system:       
    Boot sector type:  NTFS
    Boot sector info: 




================================ 1 OS detected =================================


OS#1:   Windows Recovery Environment on sda1


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: G96C [GeForce GT 120] from NVIDIA Corporation
Live-session OS is Linuxmint 64-bit (Linux Mint 21.2, victoria, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: R01-A3C0(8.15) from American Megatrends Inc.
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).






============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda	: notGPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, has-os,	has-win,	2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda1	: is-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far


Partitions info (2/3): _________________________________________________________


sda1	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	BOOTMGR,	is-winboot


Partitions info (3/3): _________________________________________________________


sda1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 0x65d11033
     Boot    Start        End    Sectors   Size Id Type
sda1           2048   30722047   30720000  14.6G 27 Hidden NTFS WinRE
sda2  *    30722048 1953521663 1922799616 916.9G  7 HPFS/NTFS/exFAT


parted -lm (filtered): _________________________________________________________


sda:1000GB:scsi:512:512:msdos:ATA WDC WD10EAVS-00D:;
1:1049kB:15.7GB:15.7GB:ntfs::msftres;
2:15.7GB:1000GB:984GB:ntfs::boot;


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda                                                                                                              
&#9500;&#9472;sda1 ntfs     E6C876E6C876B501                     65d11033-01                          PQSERVICE              
&#9492;&#9472;sda2                                                                                                           
sdb                                                                                                              
sdc                                                                                                              
sdd                                                                                                              
sde                                                                                                              


Mount points (filtered): _______________________________________________________


            Avail Use% Mounted on
/dev/sda1     3.9G  73% /mnt/boot-sav/sda1


Mount options (filtered): ______________________________________________________


/dev/sda1   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096






Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would restore the [(generic mbr)] MBR in /dev/sda, and make it boot on sda1.
Additional repair would be performed: unhide-bootmenu-10s
```


Thanks for any help
I apologise if I have posted in the wrong area.

Maxxon64

---

### Post by MAFoElffen on 2024-04-16
Welcome to Ubuntu Forums!

This will probably be moved to the Windows Section, since you only have Windows installed, (you do not have Ubuntu installed at all), and is purely a Windows Bootloader problem. 

This is an Ubuntu Linux Support Section for Users of Ubuntu. (Only)

Before they move you. Since I am a contributor to Boot-Repair: Let me answer you. That tool is to repair the Grub2 boot-loader, which most Linux systems use as a bootloader these days... If you had a Linux Distor installed, with Grub2, it would also find & load Windows.

But that is not what you have. What I see from the boot-info report is that you only have Windows installed.

Take a Windows 10 install USB, and when it gets to the first screen, selct your language & keyboard, then next. In the screen after that, instead of selecting "install", in the lower left, select the link that says "Repair your computer". (see attached screenshot). 

At the "Choose An Option" screen, select "Troubleshoot". (see attached screenshot)

At the "Advance Options" screen, select "Startup Repair". (see attached screenshot)

That should fix yours. If not, tell me.

---

### Post by QIII on 2024-04-16
Moved to Windows

---

### Post by maxxon64 on 2024-04-17
Thanks MAFoElffen for your reply. I appreciate. 
It was in fact my first attempt to use the windows tools, but it ended up with no results....it took a long time to elaborate but at the end a message indicating that the tool was not able to fix showed up; in fact I am a bit lost since I did not know what to do.
I know there are no magic solution that can fit all the issues, but I was hoping to find a way so that I used the Repair tool in order to fix it.
If you have any possible suggestion o way forward please let me know.....I will try to work on that

---

### Post by yancek on 2024-04-17
What is a 'mains problem' you refer to in your initial post?  Also, what do you mean by 'PC Repair'?  You mention win 10 in your initial post but boot repair shows you have windows vista which is long out of support so what do you actually have?  The suggestions in post 2 should work if you have the proper windows software and actually have windows 10 installed rather than vista as shown in boot repair.  You have a Legacy/CSM install so you might try an online search to repair the bootloader on vista.  It would also help if you indicate what exactly you are referring to by 'mains problem'.  What exactly happened?

As pointed out above, boot repair is only designed to repair the Grub bootloader used on Linux and although it can add a menu entry for windows, it does not and can not repair windows proprietary boot files.  If your windows files are corrupted or missing, you will need some windows boot repair tool.

---

### Post by oldfred on 2024-04-17
Windows has to have boot flag on its boot partiton.
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

You are not showing winload.exe and have boot flag on sda2s, but show bootmgr  & BCD in sda1.
You can have bootmgr & BCD in sda2, but again nothing shown.
You may need to run chkdsk or other Windows repairs.

Windows also requires the PBR partition boot sector or BS to have Windows data in it. It is different if XP or later versions of Windows. Windows will then say it is unformatted.
If chkdsk says partition is not NTFS (and report seems to say that), then you may be able to restore the backup PBR/BS.

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

Boot-Repair in its advanced mode can fix MBR. Due to copywrite, it cannot install the Windows boot loader, but the Linux syslinux boot loader works the same way, and Boot-Repair can install it. The BIOS boot loader looks for the partition with the boot flag and loads the PBR/BS for more boot code. Windows then looks for bootmgr.

Old BIOS boot process:
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)

Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since 2012 and release of Windows 8. So BIOS/MBR installs are now very rare.

---

### Post by maxxon64 on 2024-04-17
Hi Yancek thanks for replying. Let me try to explain....This broken PC, is an old one (not my actual one), with Win 10 installed. I remember that the migration was from win8  and Vista was never installed on it as far as I remember.
The mains issue happened when the system was suddenly OFF by the mains disappearing during an over-limit in my house....there were too many stuff working (washing machine etc) at the same time which forced the disconnection of the power to my house. When i tried to switching it on again the bad messages started to show up. I tried a "win fixing" using the CD bootstrap on the win 0 disk and it started to spin the diabolic round until I got the message that the WIN repair was not able to fix it. My goal is to recover picture and some files (doc and pdf) of which I have not the backup.....so a bit frustrated, my row tentative to use UBCD or PC repair without knowing well those tools.
I tried to read a bit in the web and then I was able to get the log file that I posted on my very first post yesterday night.
What would you advice.....a part trowing all in the trash bin:P?

---

### Post by maxxon64 on 2024-04-17
Hi oldfred, many thanks for the advice. Let me work on those and I will come feedback on my test results.
At this moment I cannot start windows....how can i run the CHKDSK command? by linux?
Sorry for the silly question, you may smile....but I am not a big PC expert even if i try my best
I will double check and let you know

---

### Post by oldfred on 2024-04-17
The chkdsk is a Windows only tool. You can run ntfsfix from Linux, but it only does a minor repair & turns on the chkdsk flag.

But both partition label in MBR must be NTFS and the PBR/BS must be Windows NTFS. Report seemed to say partition table showed NTFS, but details did not, which may mean PBR is damaged.

That is why I suggest chkdsk with whatever are the most recent suggested parameters for repair. And I expect it may not work, if PBR is damaged.
And then you need to see if you can restore PBR and then run chkdsk.

I once had a damaged XP NTFS. XP would not fix it, but ran Windows 7 repair disk's chkdsk. The only thing was it made the NTFS partition as as Windows 7 bootable NTFS as hidden in PBR is the file name to load. I then was able to run XP's chkdsk to fix it.
In testdisk, I could see the internal details of the PBR. And back then testdisk could also create a new PBR, but it also was the XP type. Better to use Windows tools from a Windows repair/recovery disk. And best to use same version, Windows 10 recovery  if that is what you have installed.

Repair/backup/restore
[https://www.microsoft.com/en-us/software-download/windows10ISO](https://www.microsoft.com/en-us/software-download/windows10ISO) & 
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)
Windows 10 is going to be discontinued in January 2025
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)

---

