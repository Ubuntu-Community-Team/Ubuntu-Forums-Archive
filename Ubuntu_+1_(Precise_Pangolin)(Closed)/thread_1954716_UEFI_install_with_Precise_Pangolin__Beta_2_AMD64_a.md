---
title: "UEFI install with Precise Pangolin  Beta 2 AMD64 alternate CD"
date: 2012-04-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by LazyYeti on 2012-04-08
Hello,

I'm planning to install Ubuntu 12.04 (Beta 2, alternate CD) on a brand new Lenovo X220 laptop (Intel Core i7, Intel-VT &  VT-D enabled, UEFI & legacy BIOS mode, Intel- SSD Intel 160 Go) with the following specifications :

[LIST=1]
[*]UEFI installation
[*]LVM
[*]Full disk encryption using LUKS
[/LIST]
I've downloaded & burned the Ubuntu 12.04 Precise Pangolin AMD64 alternate ".iso" [ from here]("http://releases.ubuntu.com/precise/")
I also read a little about UEFI Mode, for example [URL="https://help.ubuntu.com/community/UEFIBooting"]this ressource
[/URL]
During my first attempt, I explicitly turn off (in the Lenovo Thinkpad setup) the legacy Boot (set to UEFI only) : the system refused to boot with the Ubuntu CD. For my second attempt, I set the UEFI/Legacy Boot to "Both" and the system booted correctly on the CD.

**My questions are : **


[LIST]
[*]Does the alternate AMD 64 CD supports UEFI installation features ?
[*]If so, can I still use the manual partitionning and what are the guidelines to achieve my (2) & (3) requirements ?
[*]If not, what version of Ubuntu 12.04 do I need & what are the workarounds I could use to perform a full UEFI installation with full disk encryption & LVM ?
[/LIST]
Many thanks in advance for your suggestions

Cheers

---

### Post by den_ on 2012-04-08
Hi,

I have ASRock Extreme4  mainboard with UEFI turned on and BIOS  compatibility off. As installation media I have used Live amd64 CD.

Now IIRC during installation BIOS compatibillity was turned on, after I installed grub-efi-amd64 I shut it off. There was no need for workarounds or anything. Grub recognized also my Fedora installation on GPT parition on another disk, and my old Ubuntu 10.04 installation on MBR patitioned disk.

Here are the grub packages I have installed:
dpkg --get-selections | grep grub
grub-common					install
grub-efi-amd64					install
grub-efi-amd64-bin				install
grub-pc						deinstall
grub2-common					install

Here output of gdisk -l /dev/sda (Precise and Grub location)

GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 234441648 sectors, 111.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 1F1F813D-05A1-4E01-AF23-FD23007F0C4F
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 234441614
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048       234441614   111.8 GiB   0700  Linux filesystem

Edit:

Regarding your question about manual partitioning, yes sure you can, you only have to use a tool like gdisk which supports GPT partitions. I think I have read somewhere that gparted supports it now too, but you should check that.

Regarding full disk encryption and LVM, wasn't aware that full disk encryption is possible with linux, since you have to leave boot partition unencrypted, besides that I don't see a reason why it wouldn't work.

---

### Post by oldfred on 2012-04-08
Those that have been successful with UEFI seem to have partitioned in advance. The efi partition needs to be the first partition on the drive.

I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

More info on gdisk.
GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

Some other threads where it worked (with some difficulty)

Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
[http://ubuntuforums.org/showthread.php?t=1939094](http://ubuntuforums.org/showthread.php?t=1939094)
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)
> So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple.


An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS.


In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

Grub2 efi info ArchLinux - Arch - but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

---

### Post by LazyYeti on 2012-04-12
Thanks guys for your feedback. For a first shot, I downloaded the Ubuntu 12.04 (Beta 2) AMD64 Desktop ".iso" [here]("http://cdimage.ubuntu.com/daily-live/current/precise-desktop-amd64.iso"). 

It happened that this version is capable of booting in "UEFI Only" mode (UEFI BIOS setting + USB UEFI BIOS setting enabled), where the version I used for my first attempt (Ubuntu 12.04 Beta 2, alternate CD) couldn't boot in "UEFI Only" mode, this has been double checked... That's a start.

I wonder if the following partition scheme might be correct & optimised in term of security:

[LIST]
[*] EFI System Partition, 256MB (FAT32)
[*] BIOS Boot Partition 1MB (no filesystem)
[*][COLOR=Red]<EDIT>[/COLOR][COLOR=Red]/boot Partition  200MB (ext2)</EDIT[/COLOR]> :confused: [COLOR=Red]Finally I didn't create that one[/COLOR]
[*]/BigPartition xxx GB (to hold the encypted LVM volumes)
[/LIST]
I'm digging the EFI/UEFI litterature, those concepts are quite new for me right now, I also need to be sure about the best implementation for LUKS encryption, regarding the UEFI context...

> Regarding full disk encryption and LVM, wasn't aware that full disk  encryption is possible with linux, since you have to leave boot  partition unencrypted, besides that I don't see a reason why it wouldn't  work. @den_ : your point is correct regarding the term "Full Disk Encryption" I used in my post,  LUKS encryption is not a real FDE solution. Some workarounds might be used to harden the LUKS encryption, for instance [here]("http://xercestech.com/full-system-encryption-for-linux.geek") or[ there]("http://www.novell.com/communities/node/3357/implementing-bootcrypter-usb-tokenpassword-authentication-encrypted-hard-drives-and-swap-s"). A project called "Linux Full Disk Encryption" which seems quite dead know also drew my attention, but I digress...

Anyway I'll keep you posted until I understood how to reach my goals. :wink:

---

