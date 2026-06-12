---
title: "Grub doesn'tt load Window 10 after Window update while showing Window 10 in list"
date: 2016-09-15
forum: Windows
---

### Post by woongsim on 2016-09-15
I have installed both Window 10 and Ubuntu 16.04 in one hard drive(partitioned), and it had worked pretty well until i installed a new window update(sorry i was just routinely clicking update button, i don't remember the update name)
Grub still shows Window 10 in the OS list, but when i select it, it does not boot Window 10, and instead it just showed Grub's wine background.

I thought Grub might need to rerecognize Window 10, So in terminal i typed
> 
sudo grub-install --force /dev/sda1 
sudo update-grub

/dev/sda1 is the partition where window 10 is installed. After that command it shows

> 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.4.0-21-generic
Found initrd image: /boot/initrd.img-4.4.0-21-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 10 (loader) on /dev/sda1

Then i rebooted my computer, and select Window 10 to boot in Grub page, but now it just com back to Grub page whenever i select Window 10.
Is there any way i could fix it?

---

### Post by Bucky Ball on 2016-09-15
Welcome. You *don't* want sda1. You want to be installing grub to **_sda_**, the disk 'sda', NOT the partition 'sda1'.

I have no idea what you have on the sda1 partition but grub's there too, now. And incidentally, there should be no need whatever to --force the grub install. Leave it out.

---

### Post by woongsim on 2016-09-15
sda1 is where window 10 was installed.
Is there any way to recover sda1 and boot window10?

---

### Post by Bucky Ball on 2016-09-15
> **Bucky Ball said:**
> Welcome. You *don't* want sda1. You want to be installing grub to **_sda_**, the disk 'sda', NOT the partition 'sda1'.

Try installing grub to sda.

---

### Post by oldfred on 2016-09-15
Windows NTFS has vital boot info in the PBR - partition boot sector of all NTFS partitions.
If you forced grub to install into the NTFS PBR you broke Windows. And Windows repairs be themselves will not fix it as Windows will see it as unformatted or RAW.
NTFS does have a backup, which you often can restore.

Testdisk may say grub in PBR is valid PBR which it can be if not a NTFS partition. You want to restore a valid backup. 

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
Also check for /boot/grub in addition to /Boot

---

