---
title: "Anyone using GUID Partitioning Table"
date: 2010-10-03
forum: The Cafe
---

### Post by MooPi on 2010-10-03
I recently purchased a 1 TB drive and used GUID partition table versus MBR. Just curious if others use this and why. I'm using it based on info from the web that it's designed for larger drives and future proofed for the new EFI standard that is proposed to replace BIOS.
Before I load tons of data on this drive I thought I'd get feedback from the forum.

---

### Post by FuturePilot on 2010-10-03
I'm using it on all my external drives. Why? Because MBR is horrible. You can actually install and boot Linux from a GPT disk from BIOS. It takes a small amount of fooling around though. However Windows currently does not support booting off GPT disks.

---

### Post by oldfred on 2010-10-04
I installed it on my older 160GB drive just to test it and understand how it works. I also used it for a full install to a 16GB Flash drive. 

You need to create a bios_grub partition for grub to install correctly.

Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
Multiboot install with gpt & using gdisk
[http://ubuntuforums.org/showthread.php?t=1566090](http://ubuntuforums.org/showthread.php?t=1566090)
This link says they just installed grub2 to the drive and it found the BIOS boot partition.
[http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html](http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html)
Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
Disadvantages of hybrid gpt/MBR
[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

If you want to boot from a msdos drive also from the gpt drive (fixed in maverick):
[http://ubuntuforums.org/showthread.php?t=1405650](http://ubuntuforums.org/showthread.php?t=1405650)
Grub 2 malfunctions with a mixture of GPT and MS_DOS partition tables. But there is an easy fix, add to /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos" posted by meierfra.

---

### Post by srs5694 on 2010-10-04
I haven't checked them all, but it looks like oldfred's links provide pretty thorough coverage of the topic. I'll add that I'm the author of the [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) partitioning software, and I use GPT on several of my computers. IMHO, GPT offers minor advantages for sub-2TiB disks, but despite being minor, these advantages are great enough to favor GPT on a Linux-only system or when you're dual-booting with OSes with sufficient GPT support. GPT is a practical necessity on disks over 2 TiB in size (at least with 512-byte sectors).

Incidentally, converting back and forth between MBR and GPT is possible, with some caveats -- some disks won't convert one way or the other without resizing partitions because of the needs of each system for non-partition data storage. GPT fdisk automatically converts MBR disks to GPT when you launch it, or you can use the 'g' option on the recovery & transformation menu to convert GPT to MBR. See my [Converting to or from GPT](http://www.rodsbooks.com/gdisk/mbr2gpt.html) page for details. I mention this because of your comment about entrusting large amounts of data to GPT; if you use GPT and then find you need MBR (say, to read a disk with an old version of Windows that doesn't understand GPT), there is an "out" in the form of a GPT-to-MBR conversion. In theory, though, GPT should be more reliable than MBR, so if anything, GPT is superior from a data safety point of view.

---

### Post by MooPi on 2010-10-04
Thanks for the input everyone especially srs5694. I can now move on without reservations. The disk is for my home storage of media files and drive images (Linux only).

---

### Post by CharlesA on 2010-10-04
I've been using GUID for anything 1TB and above.

---

