---
title: "Can no longer boot from hard drive"
date: 2015-04-12
forum: Ubuntu/Debian BASED
---

### Post by GQDQALC on 2015-04-12
Hello,

I am on Elementary OS which is Ubuntu for all intents and purposes. I recently installed the newest release, but boneheadedly chose a partition (sda1) rather than the drive sda to install the bootloader to. I tried boot-repair, but it did not help. Now, I am unable to boot, and going into the BIOS it says the USB livedisk is the only boot option.

Please help.

EDIT: Here is the bootrepair output  [http://paste2.org/mAyI1wfW](http://paste2.org/mAyI1wfW) 
The OS is located on sda6. sdb is the livedisk

---

### Post by dino99 on 2015-04-12
so now boot with an iso on usb stick (or cd) and check the partition(s) with gparted: the Elementary Os partition (root) needs the 'boot' flag indeed
then to install grub on sda : sudo grub-install /dev/sda

---

### Post by oldfred on 2015-04-13
Moved to Other OS.

Are/were you booting with UEFI?
If you were booting with BIOS, you should have already had a small 1 or 2MB unformatted partition with the bios_grub flag.
And if you were booting with UEFI your efi partition was converted from FAT32 to FAT16 and now has no efi boot folders/files. Early UEFI versions of grub/Ubuntu a couple of years ago did an erase of the efi partition and conversion to FAT16, but that was fixed long ago. Do not know about Elementary and what actual version of grub2 you have.

Do you want UEFI or BIOS boot?
Remember Windows only boots from gpt partitioned drives with UEFI, and from MBR(msdos) with 
BIOS. And you cannot convert partitioning type and have Windows work.

Grub does not use boot flag. 
Windows uses boot flag with BIOS boot to know which partition has more Windows boot files. 
Gparted uses boot flag to assign the very long GUID to the efi (ESP) partition FAT 32 normally, used by UEFI with gpt partitioning to know where to look for UEFI's boot files.

---

### Post by GQDQALC on 2015-04-13
Update: I tried a clean install (i.e., backed up my files and chose install straight to the disk, rewrite the partition table). The hard drive still does not show up as an option to boot. It still can't boot.

Here is the new boot-repair report:  [http://paste2.org/gbmy1eXp](http://paste2.org/gbmy1eXp)

---

### Post by oldfred on 2015-04-13
Now you show MBR partitioning with full drive LVM logical partitioning inside the physical partitions. 
Is that what you want?
Did you run the full uninstall/reinstall of grub to MBR.
You still show an install of grub to the boot partition which never is correct, but version in MBR looks ok, if correct version for new install.

You also show two different kernels? So did you install twice with different versions using 3.13 & then 3.16 kernels?

If system is UEFI, you must make sure that all UEFI settings in UEFI are off and only CSM is on.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

