---
title: "Moving raid system to a new host"
date: 2011-08-03
forum: Server Platforms
---

### Post by pickscrape on 2011-08-03
Hi,

A while back I successfully set up a software raid (mdadm) install of ubuntu server on a cheap Compaq machine. I'm pretty sure it's running an nForce 430 chipset. Anyway, I put 3 2TB drives in it and set up two arrays: a small raid1 array for /boot and a raid5 array occupying the rest of the drives.

One point of note here is that the raid1 array never seemed to "take hold": the partition is empty, and the system has been booting entirely from the raid5 array. I'm not sure if this is relevant or not: just throwing it in there in case it is.

Anyway, I recently upgraded my desktop PC, and planned to hand down the Q6600 and DG33TL motherboard from it to the server. I did the hardware upgrade, but now the system will not boot. My question is: why.

Boot fails with the following error message:

"No bootable device -- insert boot disk and press any key"

This to me suggests that it's not even getting to the point of running grub2: the mobo itself just isn't finding anything it considers to be bootable.

I've tried all combinations I can think of of configuring the SATA support in the BIOS (modes include IDE, ACHI and RAID, all in combination with UEFI boot enabled and disabled). The system does detect the three drives: it lists them in the BIOS config screen.

I've booted from an ubuntu rescue USB drive and I'm able to see the drives and even assemble the array. I can mount the LVM partitions therein and do what I'd normally be able to do with them.

Everything *seems* fine: it just can't boot.

Grub2 is something of a mystery to me, so I'm not exactly sure what I need to do to get it booting again, if indeed it is a problem with grub.

I'm fully prepared to be sent elsewhere for suitable help on this: but I really would appreciate any pointers that anybody could give to help.

Thanks!

---

### Post by TheR on 2011-08-03
Your old system is probably booting from raid1 array. 

I don't think it is possible to boot from mdadm raid5 configuration. 

by
TheR

---

### Post by pickscrape on 2011-08-04
If that's the case, why wouldn't it just continue to boot that way after moving the drives to the new system? There's no other difference.

I've tried installing grub again on the drives to no avail. I've also tried wiping away the raid1 array and just setting them up as independent /boot partitions to see if that will at least get grub to try to boot something, but it isn't. I get the same error, which I'm pretty sure is coming from the BIOS. It's as though the BIOS doesn't even want to try and boot from the drives, even though they are definitely there and detected, as shown by the fact that I can mount them without any problems.

---

### Post by pickscrape on 2011-08-04
Furthermore, an inspection of the grub.cfg file on my drives suggests that booting from raid5 *is* possible. Things like:

```

insmod raid
insmod raid5rec
insmod mdraid
insmod lvm

```

all suggest that it should work. Furthermore, the entries themselves contain things like this:

```

set root='(raid5-root)'
search --no-floppy --fs-uuid --set <uuid here>
linux /boot/vmlinuz-2.6.35-28-server root=/dev/mapper/raid5-root ro quiet

```

This is also interesting, and shows that booting from raid5 is possible: [http://hq.sk/~r0b0/wp/21](http://hq.sk/~r0b0/wp/21)

So I'm back to my original question: why isn't the BIOS even trying to boot from any of these drives? What am I missing here?

---

### Post by srs5694 on 2011-08-04
You mention that your motherboard has a UEFI boot option. If you originally installed with an older computer, UEFI mode should be *disabled*. Alternatively, you could create an [EFI System Partition (ESP)](http://en.wikipedia.org/wiki/EFI_System_partition) on one of the disks and install an EFI-mode boot loader for Linux. This might be tricky given your configuration, though. As a stopgap measure, though, you might try creating an ESP on a USB flash drive, installing an [EFI-enabled version of GRUB 2](https://help.ubuntu.com/community/UEFIBooting) or [ELILO,](http://elilo.sourceforge.net) and see if it will boot that way. If it boots, you will at least be booting and you can deal with what to do for a long-term solution from there....

---

### Post by pickscrape on 2011-08-04
Thanks for your suggestions srs5694. I'm not sure if the old mobo supported UEFI or not, but it didn't have an option for it in the BIOS settings, so I suppose chances are that it doesn't. I did try with UEFI turned off before, but I'll try again just to be sure.

If that doesn't work, I'm going to try plugging the drives back into the original mobo to confirm that they are still indeed bootable on that machine. After that, I'll look into the other options that you've given me.

Thanks, I really appreciate it!

---

### Post by YesWeCan on 2011-08-04
What is your fdisk -l output? Have you got any boot flags set?

---

### Post by psusi on 2011-08-04
+1: probably missing partition boot flag, and new bios is a stupid one that insists that flag be set.

you definitely want UEFI boot off.

---

### Post by srs5694 on 2011-08-04
> **psusi said:**
> +1: probably missing partition boot flag, and new bios is a stupid one that insists that flag be set.

Good point; but be aware that if the disk is partitioned with the GUID Partition Table (GPT) scheme, you should *not* set a "boot flag" with parted or GParted; you should use fdisk for this task. (If the disk uses MBR partitioning, though, you can use any tool to set a boot flag, if necessary.) Seeing the "fdisk -l" output, as YesWeCan suggests, will provide necessary information if you don't know whether you've got a GPT or an MBR disk.

---

### Post by pickscrape on 2011-08-05
Thanks for your responses everyone, and sorry I'm slow with trying things as I'm working long hours at the moment and only get a bit of time in the morning to work on this. :)

So this morning I plugged the drives back into the old system and they booted fine (well, I got the grub menu, which is enough for me at this point). And I've gone the other way: plugging the Windows drive that I've created on that old system since doing this upgrade into the new board, and it boots fine, so the hardware involved is all OK.

Anyway, fsisk -l output from sda is:

```

Disk /dev/sda: 2000 GB, 2000396321280 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3               1           5       32130   83  Linux
Warning: Partition 3 does not end on cylinder boundary.
/dev/sda1               5          32      256882   83  Linux
Warning: Partition 1 does not end on cylinder boundary.
/dev/sda2              32      243202  1953263025   83  Linux
Warning: Partition 2 does not end on cylinder boundary.

```

Those errors about cylinder boundaries have been there from since the ubuntu installer created this drive. Now, sda3 is one I created after shrinking sda2 a bit to allow a bios_grub partition to be created in order to stop another grub error I was getting a while back. After fixing that though the system was fine, and booting wasn't a problem.

I'm pretty sure it is a GPT scheme, and so I've tried toggling the boot flag just now using fdisk to no avail.

I will try further suggestions this weekend.

As an aside, what's the advice on partitioning tools when it comes to cfdisk? I've always found it a lot more friendly to use than fdisk: does it handle GPT properly?

Thanks!

---

### Post by srs5694 on 2011-08-05
If that's fdisk output you've showed (and it certainly looks like it is), then the disk is definitely an MBR disk, *not* a GPT disk. AFAIK, there's no type code for a BIOS Boot Partition (what parted and GParted call a partition with a "bios_grub flag" set) on MBR disks, so there's no point in attempting to create one on your disk.

The idea of setting a boot flag (using the "a" option in fdisk, followed by "w" to save the changes) is worth trying, but from your description, it sounds like you may have already done that. It's worth double-checking that, though; a partition with the boot flag set appears with an asterisk ("*") under the "Boot" column in the fdisk partition list. Verify that it's present *and* that you've saved the partition table after making the change, then reboot and see if it works better, also being sure that the motherboard's firmware is set to BIOS (non-UEFI) boot mode.

FWIW, the "cylinder boundary" messages are harmless; they just mean that the disk was partitioned without regard for the long-irrelevant "cylinder" boundaries. Windows Vista and later, as well as most Linux partitioning tools released in the last year or two, ignore cylinder boundaries and instead align partitions on 1 MiB boundaries, which are more relevant to some types of modern disk. The latest versions of fdisk don't gripe about this any more, at least not by default.

---

### Post by YesWeCan on 2011-08-05
FYI you can also set a partition to "active" (set boot flag) using:
sudo sfdisk /dev/sda -An
Where n is the partition number. It doesnt matter which you choose for the purpose of showing your new mobo bios that the disk is bootable.

---

### Post by pickscrape on 2011-08-06
Thanks for your replies everyone.

I've done some more digging, and have determined that the drives are in fact GPT, not MBR. Here's why I say that:

```

$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 3907029168 sectors, 1.8 TiB
Disk identifier (GUID): BAC2CBB2-7155-4835-BACC-CB836BD9317C
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Total free space is 2157 sectors (1.1 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1           67584          499711   211.0 MiB   EF00  boot
   2          499712      3907028991   1.8 TiB     FD00  raid1
   3            2048           67583   32.0 MiB    EF02  

```

Parted tells me the same:

```

$ sudo parted -l
Model: ATA SAMSUNG HD204UI (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name   Flags
 3      1049kB  34.6MB  33.6MB                      bios_grub
 1      34.6MB  256MB   221MB   ext3         boot   boot
 2      256MB   2000GB  2000GB               raid1  raid


Model: ATA SAMSUNG HD204UI (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name   Flags
 3      1049kB  34.6MB  33.6MB                      bios_grub
 1      34.6MB  256MB   221MB   ext4         boot   boot
 2      256MB   2000GB  2000GB               raid3  raid


Model: ATA SAMSUNG HD204UI (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name   Flags
 3      1049kB  34.6MB  33.6MB                      bios_grub
 1      34.6MB  256MB   221MB   ext3         boot   boot
 2      256MB   2000GB  2000GB               raid2  raid

```

One thing that came to mind: the "old" mobo is actually newer than the one I'm putting in. I got the DG33TL at least a year earlier than I bought the original server hardware, so it's entirely possible that the "old" board supports newer technologies than the "new" one. My reason for the change is that the  board I'm putting in includes a CPU with double the cores and double the memory.

Anyway, with that in mind, I just did a BIOS upgrade, but it unfortunately hasn't worked. However, something interesting did happen as a result. After I'd flashed, the machine rebooted with the flash CD still in, and it booted to the ISOLINUX prompt as expected, but then after the 15-second timeout it proceeded to boot from the hard disk. The grub menu came up as usual. So the system is perfectly capable of booting from the drives, it just doesn't seem to see them initially.

I've also just had a look at the disk in the drive that the "new" board came from, which is dual-booting with Windows 7. gdisk isn't very happy about it:

```

GPT fdisk (gdisk) version 0.6.14

Type device filename, or press <Enter> to exit: /dev/sda
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by typing 'q' if
you don't want to convert your MBR partitions to GPT format!
***************************************************************

```

It works, so I've left it alone. But it's interesting that it's showing MBR, and booted with this board, while the GPT disks aren't.

So at this point I'm tempted to try backing up the GPT partition of one of the disks to a file, and converting to MBR (both using gdisk), and seeing if that disk will boot. If so, I could do the same to the rest. If not, I could restore from the backup.

Anyone have any other suggestions or think that's a bad/good idea?

Thanks!

Russ.

---

### Post by srs5694 on 2011-08-06
First, I think you need to identify why you're getting (or reporting) two entirely different and incompatible partition tables for your /dev/sda disk. In post #10, you reported:

> Anyway, fsisk -l output from sda is:

 	Code:
 	Disk /dev/sda: 2000 GB, 2000396321280 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3               1           5       32130   83  Linux
Warning: Partition 3 does not end on cylinder boundary.
/dev/sda1               5          32      256882   83  Linux
Warning: Partition 1 does not end on cylinder boundary.
/dev/sda2              32      243202  1953263025   83  Linux
Warning: Partition 2 does not end on cylinder boundary. 



fdisk doesn't understand GPT, and it would have shown a single type-0xEE partition, not three type 0x83 partitions, on a GPT disk. OTOH, in post #13, you reported an entirely different set of partitions, with both gdisk and parted showing the disk to be a GPT disk.

Were these reports on the same hard disk or on different disks? If they're different disks, as I suspect, then of course there's no problem, except that your post #10 made me think that the disk you reported there was the one that was not booting. If they're from the same disk, though, then something very peculiar indeed is going on. Please clarify.

Second, you should run the [Boot Info Script](http://sourceforge.net/projects/bootinfoscript/) on the system (with the non-booting disk installed) and post the RESULTS.txt file that it creates. This script will report more details, including the status of the boot code in the MBR and wherever that points to (if it's a valid GRUB BIOS MBR). If I'm not mistaken, that will also show the status of the MBR boot flag, which may be all you need to adjust.

Third, your gdisk and parted output makes it clear that /dev/sd?1 on your three GPT disks is a ext3 or ext4 partition but it's got the type code for an [EFI System Partition (ESP).](http://en.wikipedia.org/wiki/EFI_System_partition) This is incorrect, and it's conceivable that it's causing problems, although I wouldn't say that's anywhere near certain to be the root cause. The ESP exists to hold (U)EFI boot loader files, (U)EFI drivers, and so on. It's supposed to use the FAT32 filesystem, or at least something that the (U)EFI can understand -- certainly not ext3fs or ext4fs. One of two things is going on here, but I don't know which one:


[list]
[*]You've created ESPs and inappropriately put ext3 or ext4 filesystems on them. In this case, the EFI files probably don't exist and even if they do they are certainly inaccessible to the firmware. The appropriate fix would be to back up the ESPs, put fresh FAT32 filesystems on them, and restore the data (if any).
[*]You've created Linux /boot partitions and inapropriately marked them as ESPs (probably because of parted's use of the term "boot flag" to refer to ESPs). This seems to be the more likely explanation to me, but I can't be positive of it. The appropriate fix is to mark the /boot partitions with a correct partition type code by either removing the "boot flag" in parted or by setting the type code to 0700 or 8300 in gdisk.
[/list]


The Boot Info Script output should include /etc/fstab contents, which  will provide clues about which of these possibilities is correct.

Fourth, how did you create your duplicate partition tables for those three disks? Some methods of duplicating GUID partition tables would duplicate the disks' and/or partitions' GUIDs, which could be confusing your firmware. You can check the GUIDs with gdisk. The gdisk output you posted includes the disk's GUID:

> ```
Disk identifier (GUID): BAC2CBB2-7155-4835-BACC-CB836BD9317C

```

You can find partitions' GUIDs by using the "i" option on the main menu. It will produce output that will include a line like this:

```

Partition unique GUID: 37CE693C-386B-42EF-B481-5663E5A7A7C0
```

Every partition should have a unique partition GUID. ("GUID" stands for "globally unique identifier," after all.) Note, however, that GUIDs are also used for partition type codes; gdisk labels these as "partition GUID codes," and they'll be the same for partitions of the same type, such as A19D880F-05FC-4D3B-A006-743F0F84911E for a Linux RAID partition.

I'd put off converting from GPT to MBR until after you run the Boot Info Script, since its results may suggest a fix that's much simpler and safer. If you do end up converting from GPT to MBR, I strongly recommend you do so with the latest gdisk (0.7.2) rather than with the ancient version 0.5.1 you used to produce the partition listing in your post #13.

---

### Post by psusi on 2011-08-06
Looks like a broken hybrid setup using BOTH msdos AND GPT partition tables.  Best thing to do is blow away the GPT and fall back to a pure MSDOS setup.

---

### Post by YesWeCan on 2011-08-06
> **psusi said:**
> Looks like a broken hybrid setup using BOTH msdos AND GPT partition tables.  Best thing to do is blow away the GPT and fall back to a pure MSDOS setup.
Backup:
sudo dd if=/dev/sda bs=512 count=2048 > gptBackup.bin
Kill GPT:
sudo dd if=/dev/zero bs=512 count=1 seek=1 of=/dev/sda

---

### Post by srs5694 on 2011-08-06
> **psusi said:**
> Looks like a broken hybrid setup using BOTH msdos AND GPT partition tables.  Best thing to do is blow away the GPT and fall back to a pure MSDOS setup.

No, that's not it. Pickscrape reported the following gdisk output:

> ```
$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present
```The "MBR: protective" line clearly indicates that the disk has a valid GPT protective MBR, which is *not* what the fdisk output shows.

In the sort of situation you suggest, you'd get this instead (shown on a disk I deliberately damaged just now):

```
$ sudo gdisk -l /dev/sdc
GPT fdisk (gdisk) version 0.7.2

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: present

Found valid MBR and GPT. Which do you want to use?
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer:
```parted would also respond differently than what pickscrape reported:

```
Warning: /dev/sdc contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?
```For these reasons, I strongly suspect that pickscrape was reporting partition tables from two different disks. If that was not the case, something else was going on -- perhaps one call referenced a partition in which a partition table appeared, or maybe there's some bizarre disk hardware error that's causing improper data to be returned. (I'm grasping at straws, really.)

In any event, "blow[ing] away the GPT and fall[ing] back to a pure MSDOS setup" is inadvisable until what's really going on is ascertained with certainty. Wiping the GPT data could be extremely damaging if the computer relies on it.

[quote=YesWeCan]Backup:
sudo dd if=/dev/sda bs=512 count=2048 > gptBackup.bin
Kill GPT:
sudo dd if=/dev/zero bs=512 count=1 seek=1 of=/dev/sda     [/quote]

There are better ways to do both tasks.

The specified backup command will indeed back up the primary GPT data, but it will also back up a lot of post-partition-table data for any but a partition table that's been extended out to a huge number of entries; and it will omit the backup data. Restoring the GPT data by reversing the dd command will restore only the primary data, it might overwrite some filesystem data (if any partition begins prior to sector [noparse]2048),[/noparse] and it won't restore the backup partition data. Any of these restoration problems could cause data corruption or a need to repair the partition table.

The suggested command to destroy the GPT will only wipe the primary GPT data, leaving the backup data intact. This could conceivably cause confusion in the future, since some utilities do check for backup GPT data in case the primary data have been damaged, and might use it or at least ask you whether it should be used. After all, GPT includes backup data at the end of the disk specifically to handle damage such as an accidental use of dd wiping out the data at the start of the disk.

For both backing up and restoring GPT data, my gdisk program does a better job. The backup option ("b" on the main menu) backs up all the GPT data, including the protective MBR and both the main and backup copies of the partition metadata and data. It does this no matter what the size of the partition table, and it does *not* back up non-partition data. The restore option ("l" on the recovery & transformation menu) restores gdisk's backup files or a dd backup of the main partition data *if* it's the right size (normally 34 sectors) without writing into the sectors used by partitions (assuming the GPT data are correct, of course; all bets are off if you restore an inappropriate partition table, using any method). gdisk also includes an option to destroy GPT data, with or without also wiping the MBR (it's the "z" option on the experts' menu). This option wipes both the main and the backup partition tables. If you know the disk is an MBR disk, my FixParts program includes a somewhat easier to use and slightly safer option to wipe stray GPT data. (It's safer because there's no option to wipe the MBR, so there's less chance of user error causing unintentional damage.)

That said, I don't recommend using these options, except the backup option if the disk is a GPT disk. Keeping a backup of partition table data is always a good idea.

---

### Post by pickscrape on 2011-08-06
Thanks again for the great help I am receiving here, I really appreciate it.

Anyway, interesting things... I have created a new USB boot disk based on Natty, and have done some more tests. Note that with this boot disk, the USB drive itself is now sda, so I'm now dealing with sd[bcd]. The first thing of note is that fdisk now tells the tale you expected it to:

```

$ sudo fdisk -l /dev/sdb

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953514583+  ee  GPT

```

My previous fdisk output was definitely the same disk: there wouldn't have been any other drive available with the same layout other than the other two disks, both of which have the same output as the above.

To explain the history of the partition table a little, it was originally created by the ubuntu server installer. I used it to create two primary partitions on each disk (one small partition for the /boot raid1 array and the other for the LVM which filled the rest of the disk. Some time after I had a problem with grub: I forget the errors, but the solutions I found lead me to create the third partition by resizing and moving sd[bcd]1 and creating what is now sd[bcd]3 at the start of the disk for use by grub. This did fix the problem I was having, but I do suspect that something I did at the time is what messed things up. I honest don't remember how I made the changes though.

Anyway, natty doesn't have a more recent version of gdisk, so I've compiled it manually in order to get 0.7.2. I didn't realize you are the author, srs5694; I thank you for your help here, and for your very useful utility. The newer version adds more information to the output, but doesn't change any of the facts that it gave before:

```

$ sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.7.2

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 3907029168 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): BAC2CBB2-7155-4835-BACC-CB836BD9317C
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2157 sectors (1.1 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1           67584          499711   211.0 MiB   EF00  boot
   2          499712      3907028991   1.8 TiB     FD00  raid1
   3            2048           67583   32.0 MiB    EF02

```

The three disks do have different GUIDs. 

I attach output from boot_info_script.sh, which appears to be very thorough. :) When reading it, recall that sda is now the USB boot disk I am using.

If I may, I'd like to put forward a theory, that the problem is related to ordering. The EFI partition I created is physically the first on disk, but is listed third in many of the partition table listings, and isn't numbered consistently. For example, this is parted output:

```

Number  Start   End     Size    File system  Name   Flags
 3      1049kB  34.6MB  33.6MB                      bios_grub
 1      34.6MB  256MB   221MB   ext3         boot   boot
 2      256MB   2000GB  2000GB               raid1  raid

```

This is from RESULTS.txt:

```

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1          67,584       499,711       432,128 EFI System partition
/dev/sdb2         499,712 3,907,028,991 3,906,529,280 RAID partition (Linux)
/dev/sdb3           2,048        67,583        65,536 BIOS Boot partition

```

The order is the same, but the numbers are different. My theory is that this is the root cause: I'm very interested to know what others think (and what a potential solution could be). :)

Thanks again!

---

### Post by srs5694 on 2011-08-07
> **pickscrape said:**
> Anyway, interesting things... I have created a new USB boot disk based on Natty, and have done some more tests. Note that with this boot disk, the USB drive itself is now sda, so I'm now dealing with sd[bcd]. The first thing of note is that fdisk now tells the tale you expected it to:

```

$ sudo fdisk -l /dev/sdb

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953514583+  ee  GPT

```My previous fdisk output was definitely the same disk: there wouldn't have been any other drive available with the same layout other than the other two disks, both of which have the same output as the above.

I can't quite see how that can be. Your original fdisk output (in post #10) showed a disk size of 2000396321280 bytes, whereas this new output shows a disk size of 2000398934016 bytes -- a difference of about 2.5 MiB. Because your post #10 used cylinder units rather than sector units, it's impossible to tell if the partition start and end points match up.

In any event, lacking any good explanation, I'm going to run with the latest data you've posted and disregard that initial fdisk output. This does make me nervous, though; I can't explain that earlier fdisk output except by supposing that you're mistaken about which physical hard disk produced it.

> To explain the history of the partition table a little, it was originally created by the ubuntu server installer. I used it to create two primary partitions on each disk (one small partition for the /boot raid1 array and the other for the LVM which filled the rest of the disk.

If /dev/sd?1 are /boot partitions, then you should definitely change the partition type code, as I described in post #14 -- use parted or GParted to remove the "boot flag" or change the type code to 0700 or 8300 using gdisk. (Alternatively, if these partitions should be RAIDed, you'd want to set the "raid" flag or set a type code of FD00 -- but see below.) Linux ignores partition type codes for most purposes, but it's conceivable that incorrectly flagging those partitions as ESPs could be causing problems for your firmware, which might be trying to interpret them, failing, and then hanging as a result. This mis-typing of these partitions seems a little unlikely to me as the root cause of the problem, but not impossible.

If you believe this separate set of /boot partitions to be RAIDed, this seems to be at least partly incorrect. According to the Boot Info Script output, /dev/sdb1 and /dev/sdd1 are both ext3, whereas /dev/sdc1 is a Linux RAID member, and the parted output you posted in post #13 suggests that /dev/sdc1 (/dev/sdb1 in post #13) uses ext4. These inconsistencies were probably caused by the partition resizing you mentioned, but if they worked on one motherboard, they would most likely not be the root cause of the inability of the firmware to begin the boot process on this other board. Thus, although fixing these problems in one way or another should be on your agenda of things to fix, I don't recommend messing with it just yet; get the system booting first and *then* fix the RAID/non-RAID status of /boot.

> Some time after I had a problem with grub: I forget the errors, but the solutions I found lead me to create the third partition by resizing and moving sd[bcd]1 and creating what is now sd[bcd]3 at the start of the disk for use by grub. This did fix the problem I was having, but I do suspect that something I did at the time is what messed things up. I honest don't remember how I made the changes though.

You created a BIOS Boot Partition and duplicated it on all the drives. This is a necessary fix for certain GRUB issues on GPT disks on BIOS-based computers, and it's almost certainly *not* the source of the problem you're experiencing now. Unless I'm overlooking something, your Boot Info Script output suggests that a BIOS-mode GRUB is properly installed on your disks.

> The three disks do have different GUIDs.

That's reassuring.

> If I may, I'd like to put forward a theory, that the problem is related to ordering. The EFI partition I created is physically the first on disk, but is listed third in many of the partition table listings, and isn't numbered consistently.

No, that's not the issue. Your partitions *are* numbered consistently across disks, and the fact that partition numbers don't match on-disk order is irrelevant. I suspect you're getting confused by the MBR's 0xEE partition, which has nothing to do with the *real* partitions, which are defined in the GPT. The 0xEE partition exists only to try to keep GPT-unaware tools from messing with the disk; with a proper 0xEE partition in place (which you've got on all your disks), the disk will appear to be completely in use to MBR-only utilities.

My suspicion is that the problem is the lack of a boot flag on the 0xEE partition. Some BIOSes have bugs that cause them to be unable to boot from a hard disk if the MBR has no partitions that are marked as bootable. On a GPT disk, the MBR is a protective MBR that, as I've just said, contains a single type-0xEE partition that fills the disk. This partition is not normally marked as being bootable, but with some BIOSes, it must be so marked in order for the BIOS to boot.

To fix this problem, you should use fdisk to set the boot flag on the 0xEE partition on at least one of your disks. Use the "a" option to set the flag, then use "w" to save the change, then verify that it's been set (say, by typing "fdisk -l"). Once that flag is set, if this hypothesis is correct, then the computer will begin booting normally -- or at least, you'll get to GRUB and be able to select your kernel. (It's conceivable it'll fail to boot completely because of hardware changes, but if so that'll be an entirely different problem.) You may need to explicitly disable UEFI boot support in your firmware setup utility.

Note that you must use fdisk or some other non-GPT tool (cfdisk or sfdisk) to set the boot flag. The parted and GParted programs won't let you modify the MBR on a GPT disk. If you use them to set a "boot flag" on a GPT disk, these tools interpret it as a request to change a *GPT* partition (not the MBR's protective partition) to be an ESP. It's unfortunate that the libparted developers chose to use the same term ("boot flag") for entirely different and incompatible concepts on MBR and GPT disks.

---

### Post by pickscrape on 2011-08-07
First, regarding the messed up raid1 array: that was me playing before I started asking for help. My theory at the time was that for some reason the new board wasn't picking up the raid, so I tried taking it apart and creating plain /boot partitions instead as an experiment. When that didn't work, I figured something more fundemental was the issue. I agree entirely that sorting that after boot itself works is definitely the best way forward. As I said earlier, I'm pretty sure that the system was actually getting everything from the raid5 array anyway, so I don't think it's much of a loss.

Your latest post has made the penny drop for me regarding the protective MBR and its relationship with GPT: it all makes sense now. And as a result I have good news: enabling the boot flag on the EE partition in fdisk was all that was needed to get the system seeing the disk as bootable. Interestingly, I tried it with one drive at first, and while grub did boot, the system was unable to build the array and boot the OS. In order for that to work, I had to set the MBR partition boot flag on all three drives. I'm not sure if that's something that always happens, but I though it was interesting nonetheless. The system then booted fully. I did get some odd EOFBLOCK_FL output while the system was fsck-ing the LVM /var partition, but everything that uses stuff in there seems to be happy.

I'm *extremely* happy that this ended up having a simple solution. srs5694: I can't thank you enough. I often find that I get few or no responses to things I ask about online (probably because they're usually quite obscure problems), but you've given me a lot of your time and excellent advice to go with it. I would probably have opted for some sort of clean install solution had it not been for your help. Thank you so much!

---

### Post by YesWeCan on 2011-08-07
> **srs5694 said:**
> There are better ways to do both tasks.
It doesn't matter. Why use an espresso machine to make coffee when instant will do (in this particular case)?

> The specified backup command will indeed back up the primary GPT data, but it will also back up a lot of post-partition-table data for any but a partition table that's been extended out to a huge number of entries; and it will omit the backup data.
So?
> Restoring the GPT data by reversing the dd command will restore only the primary data, it might overwrite some filesystem data (if any partition begins prior to sector [noparse]2048),[/noparse] and it won't restore the backup partition data. Any of these restoration problems could cause data corruption or a need to repair the partition table.
I gave a backup solution. I haven't mentioned restore yet.
> The suggested command to destroy the GPT will only wipe the primary GPT data, leaving the backup data intact. This could conceivably cause confusion in the future, since some utilities do check for backup GPT data in case the primary data have been damaged, and might use it or at least ask you whether it should be used. After all, GPT includes backup data at the end of the disk specifically to handle damage such as an accidental use of dd wiping out the data at the start of the disk.
Clutching at straws here. Once the GPT header is gone then nothing matters unless one deliberately seeks to reconstruct the GPT with a specialised tool.

> For both backing up and restoring GPT data, my gdisk program does a better job.
;) I'm sure it makes great coffee.

---

### Post by srs5694 on 2011-08-07
> **YesWeCan said:**
> [quote=srs5694]There are better ways to do both tasks.It doesn't matter. Why use an espresso machine to make coffee when instant will do (in this particular case)?

> **srs5694]The specified backup command will indeed back up the primary GPT data,  but it will also back up a lot of post-partition-table data for any but a  partition table that's been extended out to a huge number of entries said:**
> 

So?

[quote=srs5694]Restoring the GPT data by reversing the dd command will restore only the  primary data, it might overwrite some filesystem data (if any partition  begins prior to sector 2048), and it won't restore the backup partition  data. Any of these restoration problems could cause data corruption or a  need to repair the partition table. 			 		

I gave a backup solution. I haven't mentioned restore yet.[/quote]

A backup solution without a matching restore solution is useless, and understanding the potential problems with the full backup/restore operation should clarify the earlier points. Some things that can go wrong with a simple dd backup of the first 2048 sectors include:


[list]
[*]If the GPT supports a huge number of partitions (more than 8184), then a simple dd backup of 2048 sectors will omit some of those partitions. Even if partitions beyond #2048 aren't used (but are defined in the GPT), restoring them will leave whatever had been in those sectors intact, which could result in a corrupt GPT if those sectors change between the backup and the restore. I grant that this type of problem is unlikely to occur in the real world, since extending the GPT beyond 128 partitions is rarely done; however, it *can* occur, and there are occasionally weird setups, so a solution that ignores this possibility is risky.
[*]By not backing up the backup GPT data at the end of the disk, you'll be unable to restore it. This means that if you back up the primary GPT data, make changes to the partition table using a partitioning tool, and then restore the primary data, the primary and backup data will be out of sync with each other. Since the purpose of the backup partition table is to hold an accurate representation of what's in the primary, at the very best this is a dangerous inconsistency. At worst, some tool or OS could become confused by it. (I just checked, and neither gdisk nor parted detects this inconsistency. I intend to fix this oversight in gdisk with the next version.)
[*]By not backing up the backup GPT, if the backup GPT data are erased and a restore attempted, the GPT data set will be incomplete. Most GPT tools should be able to recover from this problem, but they shouldn't have to do so, and it's conceivable that some will crash or otherwise misbehave. (Both gdisk and parted do the recovery properly, though.)
[*]If the primary partition table were damaged in some way but the backup was OK, then backing up the primary table only would risk losing the correct data in the backup.
[*]Assuming a typical 128-partition GPT and 512-byte sectors, backing up 2048 sectors backs up data that's *not* part of the partition table. If a partition began in that space (as is quite common), then restoring the data would also restore the partition's data, which could result in filesystem corruption if that partition had been modified between the backup and the restore. This problem can at least be overcome by restoring only the correct number of sectors, but if you don't know that value (and you couldn't know it with certainty without examining the data in the backup), or if you forget to make the adjustment, you risk damaging filesystem data. If you *do* know the value, then it's much safer to back up only the required number of sectors to begin with.
[/list]


Thus, a simple dd backup of the primary partition table alone is riddled with problems. Writing a script to do it properly shouldn't be too hard, though; you'd need to interpret enough of the GPT data to figure out its size, and therefore the number of sectors to back up; then back up both the primary and backup data. Reversing the process would be similar for the restore. A well-written script would be superior because it reduces the odds of human error creeping in and causing data loss.

As I said, gdisk does the job properly, too, although there is a caveat: gdisk backs up GPT data as stored in memory. If the partition table was damaged in some way, then gdisk might make changes in memory to fix the problem, and so the backup wouldn't be an exact representation of what's on the disk. In such a case, using dd (but in a more complex way than you suggested) might be worthwhile, in case gdisk's interpretation of the damaged disk was incorrect.

[quote=YesWeCan][quote=srs5694]The suggested command to destroy the GPT will only wipe the primary GPT  data, leaving the backup data intact. This could conceivably cause  confusion in the future, since some utilities do check for backup GPT  data in case the primary data have been damaged, and might use it or at  least ask you whether it should be used. After all, GPT includes backup  data at the end of the disk specifically to handle damage such as an  accidental use of dd wiping out the data at the start of the disk. 			 		[/quote]

Clutching at straws here. Once the GPT header is gone then nothing matters unless one deliberately seeks to reconstruct the GPT with a specialised tool.[/QUOTE]

In theory and if the MBR doesn't contain a 0xEE partition, then yes, the presence of backup GPT data shouldn't be a problem. If the MBR does contain a 0xEE partition, though, then a good GPT-aware utility should search for and load the backup GPT data if the primary GPT data are found to be corrupt or missing. (gdisk does this, but parted doesn't.) I also wouldn't rule out the possibility of problems from utilities that do very extensive probing even if the MBR contains no 0xEE partition. fdisk and gdisk both do detect the backup GPT data and notify the user of its presence even if there's no 0xEE partition in the MBR. This is likely to cause confusion if the backup GPT data are spurious, but of course they both do so because that can't be certain -- it could be that the backup data remain after some partitioning disaster. parted does not check for the backup GPT data when the MBR has no 0xEE partition; it uses the MBR data alone. I don't know how other tools (Windows' disk partitioner, OS X's Disk Utility, etc.) respond to this type of condition. I wouldn't want to rule out the possibility that one of them would do something very weird.

The bottom line: If you want to do a job, do it right. The dd command you suggested to back up GPT data is inadequate, as is the dd command you suggested to destroy GPT data. Both jobs *can* be done with dd, but you'd need a more complex command -- or better yet a shell script -- to do it right.

---

### Post by YesWeCan on 2011-08-08
Are you paid by the word? You write books and articles, so you probably think you are! :P

Your arguments are pedantic and not important in the case of this thread. And you are unreasonably criticising my method.

Why can't you just accept that there are other ways to do a perfectly adequate job than using your tool?

If your response had been - "yes, those dd command will back up the GPT data and yes will render the disk GPT-less and it is very quick, but there is a tool that can do it in a way that makes restore easier (in the unlikely event that the OP would want to do a restore)" then that would have been respectful and informative and accurate. But instead you weave a long diatribe of exaggerated criticisms of my method as if to try to filibuster yourself into being right.

Why do you do this?

I could go through your last post and refute it point by point but it is not worth my time. And I am not going to respond any further to this post. :|

---

### Post by srs5694 on 2011-08-08
> **YesWeCan said:**
> Your arguments are pedantic and not important in the case of this thread. And you are unreasonably criticising my method.

I didn't make my last post for pickscrape's benefit, since (s)he has said that the original problem is solved. I posted in order to clarify for other readers (now or in the future) why a simple dd backup of GPT data is inadequate, and why backing up (or more to the point, restoring) too many sectors is risky. Whatever you may think, these are not "unreasonable" criticisms.

Much of what I believe you consider "pedantic" is in direct response to your query of "so?" (in post #21) to my earlier statement (in post #17) that your suggested dd command backs up too much data from the start of the disk and omits the backup data. *You* asked why those factors were important, so I replied.

> Why can't you just accept that there are other ways to do a perfectly adequate job than using your tool?

There *are* other ways to do it. As I wrote in my last post, a script that backed up the correct data would do it. Perhaps some other partitioning tool includes a GPT backup facility and I don't know what it is. As I detailed, though, a simple dd operation is ***not*** "perfectly adequate." At best, it will work in some circumstances; but if you don't fully understand what those circumstances are, using a simple dd backup of the first few sectors of a disk is a risky way to back up GPT data.

> If your response had been - "yes, those dd command will back up the GPT data and yes will render the disk GPT-less and it is very quick, but there is a tool that can do it in a way that makes restore easier (in the unlikely event that the OP would want to do a restore)" then that would have been respectful and informative and accurate. But instead you weave a long diatribe of exaggerated criticisms of my method as if to try to filibuster yourself into being right.

Why do you do this?

You're advocating a dangerous method that, if followed by a less-knowledgeable person, could easily lead to data loss.

Please don't mistake a correction for disrespect. This forum is filled with posts that are followed by other posts that correct errors in the original post. I've both posted corrections and been corrected by others. Such corrections do not imply, by themselves, disrespect, nor do they constitute a "diatribe" -- although I admit my post was long. You asked a deceptively simple question ("so?"), but to adequately explain *why* those factors were important took a while.

---

