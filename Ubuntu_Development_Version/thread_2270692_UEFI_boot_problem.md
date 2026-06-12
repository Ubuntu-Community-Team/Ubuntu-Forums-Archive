---
title: "UEFI boot problem"
date: 2015-03-24
forum: Ubuntu Development Version
---

### Post by 00b00nt00 on 2015-03-24
Now my mobo won't initialise a UEFI boot from optical media, so using Rufus on Windows I created a UEFI bootable USB dongle of the latest Vivid daily.

The live boot is fine, and I am able to install Vivid on to the HDD which it has all to itself. Upon rebooting, I get the "insert bootable media" error, and the only way I can get the system to boot from the HDD is if I go into the BIOS and switch the system to a legacy boot.

I've then started the live USB again and examined the partitions using Gparted: sda1 is a 512mb (give or take) fat32 partition with boot, efi flags enabled; sda2 is the lion's share of the HDD and sda3 is devoted to the swap file.

14.04 and 14.10 both boot fine after installation. What gives?


990fxa-uda5 v. 3.0

---

### Post by grahammechanical on 2015-03-24
> [COLOR=#000000]14.04 and 14.10 both boot fine after installation. What gives?[/COLOR]

Do you have 14.04 and 14.10 on this machine? I have no experience with UEFI but as I understand things if the system is set to EFI (not legacy) and Ubuntu is installed in EFI mode, then switching to legacy mode should not load Ubuntu. The fact that Vivid loads when switched to legacy mode causes me to wonder if Vivid was not installed in EFI mode as it should have been.

If you installed 14.04 and 14.10 as an experiment and you installed them in EFI mode then that would have created sda1 as an efi partition but the existence of an efi partition does not in itself convince me that Vivid was installed in EFI mode.

Regards.

---

### Post by ventrical on 2015-03-24
Depending on the Motherboard type you could try to go to UEFI Boot Menu (some machines F10.. others F11) and you should be able to see the [ubuntu] device to boot.

Also .. when using your boot menu you have to be specific when you install into UEFI mode. it wil give you those options from USB and boot right into Grub.

Regards..

---

### Post by oldfred on 2015-03-24
May be best to see details, run summary report and post link it gives.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you have more than one drive, do not run auto repair. Only advanced repair should be used with advanced configurations or anything more than Windows & Ubuntu on one drive.

---

### Post by 00b00nt00 on 2015-03-25
> Do you have 14.04 and 14.10 on this machine? I have no experience with UEFI but as I understand things if the system is set to EFI (not legacy) and Ubuntu is installed in EFI mode, then switching to legacy mode should not load Ubuntu. The fact that Vivid loads when switched to legacy mode causes me to wonder if Vivid was not installed in EFI mode as it should have been.

If you installed 14.04 and 14.10 as an experiment and you installed them in EFI mode then that would have created sda1 as an efi partition but the existence of an efi partition does not in itself convince me that Vivid was installed in EFI mode.

I erased the HDD using Killdisk so only Vivid is installed.

Vivid, 14.04 and 14.10 have all been installed (at different times) using a UEFI bootable USB dongle. Of these, only Vivid has subsequently refused to boot from the HDD in UEFI mode.

I'd like to use Vivid as it resolves the eSATA / IOMMU bug present on AM3+ boards whereby external disks conected via eSATA won't mount.

>  Depending on the Motherboard type you could try to go to UEFI Boot Menu (some machines F10.. others F11) and you should be able to see the [ubuntu] device to boot.

Also .. when using your boot menu you have to be specific when you install into UEFI mode. it wil give you those options from USB and boot right into Grub.

The only option I see on pressing F12 is to enter the BIOS (unless the dongle is plugged in), and that doesn't work unless I reboot and hit DELETE because of some bug (thanks, Gigabyte).

> Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:

Tried it. I'm posting here as a last resort. Boot Repair won't fix the disk claiming that there is no bootable partiton and that I should go into Gparted and create a FAT32 partiton and set the boot flag. Helloooo - yes there IS a damn FAT32 partition with the boot flags set!

What I have noticed is that Vivid does name the bootable EFI partition differently from previous versions of Ubuntu. I don't see why that should make a difference, though.

---

### Post by oldfred on 2015-03-25
Please do not run Boot-Repair but post link to Summary report, so we can suggest which Advanced mode Boot-Repair fix or other fixes that may be required.

---

