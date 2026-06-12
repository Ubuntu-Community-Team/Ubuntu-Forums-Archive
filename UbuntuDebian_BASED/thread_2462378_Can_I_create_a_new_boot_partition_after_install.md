---
title: "Can I create a new boot partition after install?"
date: 2021-05-19
forum: Ubuntu/Debian BASED
---

### Post by on-the-beach60 on 2021-05-19
After losing access to Ubuntu following a Win10 update, I loaded boot-repair on a live USB and ran Boot-info.   A recommendation in the file was to create a boot partition at the start of the disk because my bios may not detect the boot files in their current location.   Then perform the boot-repair.

I'm not experienced with gParted.   If I create a new boot partition will it destroy my Win10 or Ubuntu installs?    Is there a case where I should manage the partitions from Windows?

The boot info file can be found at paste.Ubuntu.com/p/6YdNCGjVgF/

---

### Post by ubfan1 on 2021-05-19
You have a legacy install of Windows10 (on an msdos partition type disk), so no EFI partition is needed.  You have an unformatted EFI partition at the end, but that was never used.  If you were booting before successfully, I'd just reinstall grub from the install media again -- looks like Windows replaced the MBR bootloader (grub) with its own bootloader. Do not make any new partitions, you don't need any, and you can mess up Win10.

---

### Post by Impavidus on 2021-05-19
> **on-the-beach60 said:**
>   A recommendation in the file was to create a boot partition at the start of the disk because my bios may not detect the boot files in their current location.

That's a recommendation because on some old systems the bios may be unable to load the necessary parts of the bootloader when they are too far from the start of the disk, as the bios can't handle such large disks. So the early stages of booting must all be stored near the start of the disk, and those early stages of booting are more capable than the bios and can access the far parts of the disk to fetch the next stage of booting. As your system worked before, it doesn't apply to you.

Now it is somewhat weird that you have grub installed in the partition boot record of an ntfs partition. Normally, we never install grub in a partition boot record. sda3 is a superfluous efi partition, but should be ignored. OS proper detects Windows, so that's good. Otherwise you have to boot Windows and make sure that fast startup has been disabled, or grub is unable to boot Windows. Boot-repair should be able to reinstall grub to the master boot record. I think the default repair will do just that.

These systems with dual booting Ubuntu and Windows 10 in legacy mode are a bit fragile.

---

### Post by oldfred on 2021-05-19
It also looks like you have installed grub to partition boot sector (PBR or BS) of sda2. Grub should only be installed in MBR of a drive, not to a partition. You can use Boot-Repair's advanced mode or manual commands to install grub to MBR. Also have a Windows repair/recovery flash drive to make Windows repairs. Grub only boots working Windows. If Windows is hibernated (or fast start sets hibernation flag) or it needs chkdsk, grub will not boot Windows. Then you have to repair Windows. You may be able to put Windows boot loader into MBR and f8 into repair console or use repair flash drive. And then restore grub to MBR.
This is part of the hassle with Windows 10 in BIOS/MBR configuration. Microsoft has required vendors to install in UEFI/gpt mode and then you can always directly boot all installs from UEFI boot menu. But it does allow the old BIOS type install, but then is not dual boot friendly.


Windows has essential info in the PBR of any NTFS partition. It will not run chkdsk on it as it will see it as RAW.
Boot-Repair may say it is ok, as grub in a PBR of Linux partition can be valid but is never recommended.

You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyze] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by coffeecat on 2021-05-19
Bodhi Linux. *Thread moved to the **Ubuntu/Debian Based** sub-forum.*

---

### Post by on-the-beach60 on 2021-05-19
Thank you.  Boot repair was successful.

---

### Post by on-the-beach60 on 2021-05-19
Thank you.  Boot repair reloaded grub2 into the MBR and I can now access Linux and Windows.

---

