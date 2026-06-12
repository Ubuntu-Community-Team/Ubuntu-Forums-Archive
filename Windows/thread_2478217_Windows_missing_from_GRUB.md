---
title: "Windows missing from GRUB"
date: 2022-08-19
forum: Windows
---

### Post by insipidboar on 2022-08-19
I could have sworn I followed dual boot install correctly but windows is gone.


Ran fdisk- no Microsoft data on any sdas 


```
Ran os-prober, 
update-grub, 
set GRUB_DISABLE_OS_PROBER=false in nano
cat /etc/default/grub
nano /etc/default/grub
update-grub


No luck&#8230;..

I then was suggested to run a boot repair (2nd option) this was at the end of my [HTML]https://paste.ubuntu.com/p/JdBxWFFrrq/[/HTML]:
I do not really understand the suggested directions.

Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would purge [COLOR=#666666]([/COLOR]in order to remove grub-efi[COLOR=#666666])[/COLOR] and reinstall the grub2 of
sda5 into the MBR of sda.
Grub-efi would not be selected by default because legacy Windows detected.
Additional repair would be performed: unhide-bootmenu-10s

Blockers in [COLOR=#AA22FF]**case**[/COLOR] of suggested repair: __________________________________________

LegacyWindows detected. Please [COLOR=#AA22FF]enable[/COLOR] BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD [COLOR=#666666]([/COLOR]or live-USB[COLOR=#666666])[/COLOR]. Please use this software in a live-session [COLOR=#666666]([/COLOR]live-CD or live-USB[COLOR=#666666])[/COLOR]. This will [COLOR=#AA22FF]enable[/COLOR] this feature.

Confirmation request before suggested repair: __________________________________

LegacyWindows detected. The boot of your PC is in EFI mode. You may want to retry after changing it to BIOS-compatibility/CSM/Legacy mode.
Are you sure you want to [COLOR=#AA22FF]**continue**[/COLOR] anyway?

Final advice in [COLOR=#AA22FF]**case**[/COLOR] of suggested repair: ______________________________________

Please [COLOR=#AA22FF]**do**[/COLOR] not forget to make your BIOS boot on sda [COLOR=#666666]([/COLOR]ATA SATA SSD[COLOR=#666666])[/COLOR] disk!
The boot of your PC is in UEFI mode. You may want to retry after changing it to BIOS-compatibility/CSM/Legacy mode.
```

---

### Post by oldfred on 2022-08-19
Please use Code Tags if posting terminal output.
How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

At least two major issues.
You cannot mix UEFI boot with BIOS boot.
You cannot install grub to NTFS partition as that wipes the vital NTFS boot info in the partition boot sector(BS or PBR).

Microsoft has required Windows to be installed in UEFI boot mode to gpt partitioned drives since 2012. You have Windows installed in BIOS boot mode to MBR partitioned drive. Did you incorrectly install it yourself?

In BIOS boot mode, Windows has to have boot flag on the NTFS partition with boot files, your sda1.
But UEFI has boot flag on the ESP - efi system partition your sda3.
But only one boot flag per drive, so if you want BIOS boot, move boot flag back to sda1 with gparted.
You can erase sda3.

You then have to repair NTFS partition. It probably has backup, so you can restore the Windows data to BS.
[http://www.ntfs.com/fat-partition-sector.htm](http://www.ntfs.com/fat-partition-sector.htm)
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

You may have to use your Windows repair flash drive to restore Windows boot loader to MBR.
Make sure Windows boots & that you have Windows fast start up off.
Then use Boot-Repair to install grub to MBR & grub should then be able to boot both systems.

But Windows turns fast start up back on with updates. Then grub will not boot Windows.
You have to temporarily restore Windows boot loader, fix Windows & restore grub.

Better to install Windows in UEFI boot mode with gpt drive.
But conversion from MBR to gpt will erase drive, so make sure you have good backups.

---

### Post by insipidboar on 2022-08-21
Thank you I will give this a shot tomorrow and report back. I appreciate your time!

---

