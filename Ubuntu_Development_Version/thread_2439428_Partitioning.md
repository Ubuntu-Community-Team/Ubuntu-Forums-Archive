---
title: "Partitioning"
date: 2020-03-27
forum: Ubuntu Development Version
---

### Post by P-I H on 2020-03-27
I installed iso20200325 and iso20200326 on an older computer without UEFI support with one SSD and one HD.
I used the Erase Disk method and expected to get partition 1 for the boot files and partition 2 for the system.
However I got Partition 1 för the boot files, an Extended Partition 2 and Partition 5 for the system. I have never seen this before and the EFI folder is empty.
Is Ubiquity changed to give this kind of strange partitioning?

---

### Post by oldfred on 2020-03-27
It looks like you installed in UEFI boot mode to a MBR partitioned drive.
Post these, I expect parted to say MSDOS/MBR and fstab to show mount of ESP:
sudo parted -l
cat /etc/fstab

You do not see files in ESP. 
If you look at fstab you will see the mount of your ESP. It will have permissions of umask=0077 where before 14.04 it used defaults. When you run Boot-Repair it also changes to defaults, so it can edit the ESP files.
I also change to defaults, but that may be a security issue and may change back to 0077.

---

### Post by P-I H on 2020-03-28
Perhaps I haven't noticed this before, but why doesn't an installation with "Erase disk" create a "better" partitioning.
I had W10 installed on this computer earlier. Perhaps that's the reason why /boot/efi is formatted as vfat.
I will check two things and see what's happening
- Install with an earlier iso
- Format the disk before installation
```
p-i@pi-GA-990FXA-UD3:~$ sudo parted -l
[sudo] password for p-i: 
Model: ATA KINGSTON SV300S3 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 
Number  Start   End    Size   Type      File system  Flags
 1      1049kB  538MB  537MB  primary   fat32        boot
 2      539MB   120GB  119GB  extended
 5      539MB   120GB  119GB  logical   ext4
Model: ATA WDC WD6400AAKS-0 (scsi)
Disk /dev/sdb: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 
Number  Start   End    Size   Type     File system  Flags
 1      1049kB  640GB  640GB  primary  ext4         boot

p-i@pi-GA-990FXA-UD3:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=c0acf1e4-0b1e-49b0-824e-e9db9ca1c156 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=441D-FD7E  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
p-i@pi-GA-990FXA-UD3:~$
```

---

### Post by oldfred on 2020-03-28
You have UEFI install to MBR(msdos) partitioned drive.

Much better to use gpt.
Gparted still defaults to using MBR on smaller drives, you have to change to gpt if formatting in advance.

Installer must have seen MBR, otherwise I believe it would have used gpt with UEFI as that is the recommendation.
Windows will only install in UEFI mode to gpt drives.

PT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Gigabyte GA-990FXA-UD3 and 64bit Xubuntu 16.04 LTS install
[https://ubuntuforums.org/showthread.php?t=2370503](https://ubuntuforums.org/showthread.php?t=2370503)

---

### Post by P-I H on 2020-03-28
Made some test.
Formated the ssd with Disks to "No partitioning (Empty) and started an installation. No change still made an extended partition.
Formated with GPT and Ubiquity still made an extended partition.
Continued the installation and in this case the installation crashed.
Made a new USB installation device with iso20200327 which also crashed at installation. Got the message about already known bug.
There is however an MBR on the HDD, but does this have any impact?

---

### Post by oldfred on 2020-03-28
The gpt partitioning has a protective MBR. That has one entry for gpt for entire drive if less than 2TiB, or is 2TiB, so old MBR based tools do not automatically assume drive is empty and partition/format it.

What does this show?
sudo gdisk -l /dev/sda

I have always partitioned in advance with gpt & usually several partitions and never have had an issue. But I use gparted as Disks has in past had some issues. I do use Disks only to label partitions when I forget to label using gparted.

---

### Post by P-I H on 2020-03-29
```
p-i@pi-GA-990FXA-UD3:~$ sudo gdisk -l /dev/sda
[sudo] password for p-i: 
GPT fdisk (gdisk) version 1.0.5

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sda: 234441648 sectors, 111.8 GiB
Model: KINGSTON SV300S3
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 91B70B2A-F1AD-498C-8AB6-0556644E4A2C
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 234441614
Partitions will be aligned on 2048-sector boundaries
Total free space is 4973 sectors (2.4 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1050623   512.0 MiB   0700  Microsoft basic data
   5         1052672       234440703   111.3 GiB   8300  Linux filesystem
p-i@pi-GA-990FXA-UD3:~$ 
```
As you suspected Disks didn't partitioned sda properly.
Anyhow I don't understand why Ubiquity don't prepare the disk correctly when "Erase disk" is used.

Made a new iso, booted and used gparted to clean sda. Started an install, but sda was still partitioned with an extended partition.
Checked sda and there is still a protective MBR.
```
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 234441648 sectors, 111.8 GiB
Model: KINGSTON SV300S3
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 400D9BD0-9398-43E5-9FC4-A86EF5C06992
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 234441614
Partitions will be aligned on 2048-sector boundaries
Total free space is 234441581 sectors (111.8 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
ubuntu@ubuntu:~$ 
```

---

### Post by sudodus on 2020-03-29
What would happen if you wipe the whole device (overwrite it with zeros for example with mkusb)? Then there should be no traces on the drive to tempt the installer to create an MSDOS partition table. So if that still happens, it is the default behaviour, at least in this older computer without UEFI support.

By the way, maybe it is worth testing that in a computer where you can select both boot modes. If you do that, is there a difference between the partition table created in UEFI mode and BIOS mode (alias CSM alias legacy mode)?

---

### Post by oldfred on 2020-03-29
> Found valid GPT with protective MBR;

That says sda is gpt partitioned.

---

### Post by P-I H on 2020-03-29
Done that with Disks and this cleaned the disk.
sudo gdisk -l /dev/sda gave the result
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present
However even now an extended partition was created when "Erase Disk" was used.
Tried with something else and selected the whole disk. This worked, got one partition which included a MBR.
Booted with the USB again. Used gparted this time, made a GPT partition table and a fat32 partition. Installed with the "Something Else" method. This time I got /dev/sda1 fat32 and /dev/sda2 ext4.
However Ubiquity didn't use /dev/sda1, perhaps because I didn't set any flags.
It seems to be quite complicated to manage the boot records. In case you have a dual boot with W7 and Ubuntu and want to reinstall Ubuntu, the protective MBR is needed. In case you want to install W10 and Ubuntu in UEFI mode I suppose you need to overwrite the disk with zeros and this will take some time.
The system I used have a HDD with Ubuntu 19.10 installed in legacy mode, that may also have some impact.

This is information from the actual system

---

