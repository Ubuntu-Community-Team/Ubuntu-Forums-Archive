---
title: "BIOS/UEFI settings to recognize M2 SSD for Windows 10 install?"
date: 2016-12-04
forum: Windows
---

### Post by kc_2 on 2016-12-04
[COLOR=#272A34][FONT=&amp]I'd like to set up the new computer to recognize the M2 SSD as a bootable device so I can install Windows 10 on it. How do I do that?

[/FONT][/COLOR][COLOR=#272A34]Edit - I also want to use the motherboard's RAID. I noticed I have to disable it for it to recognize the M2. I'm hoping I can still re-enable it and use it after I install the system, without losing the ability to boot into the system.[/COLOR]

---

### Post by oldfred on 2016-12-05
How would you use RAID if you have one M2 SSD?

Is drive just M.2 or also NVMe?

Windows should just install. But you have to boot the Windows flash drive in UEFI mode to install in UEFI mode or boot installer in BIOS boot mode to install in BIOS. Drive must be MBR(msdos) partitioned if using BIOS.
Better to use UEFI if newer system. And Windows only boots in UEFI mode from gpt partitioned drives.

       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by kc_2 on 2016-12-05
> **oldfred said:**
> How would you use RAID if you have one M2 SSD?

m2 ssd is not in the raid, it is an OS disk that will access the raid.

> Is drive just M.2 or also NVMe?

also nvme

> Windows should just install. But you have to boot the Windows flash drive in UEFI mode to install in UEFI mode or boot installer in BIOS boot mode to install in BIOS. Drive must be MBR(msdos) partitioned if using BIOS.
Better to use UEFI if newer system. And Windows only boots in UEFI mode from gpt partitioned drives.

I just used the auto-detect option. I might actually reinstall the OS but making sure the install usb is using uefi.

> Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

going raid1

---

