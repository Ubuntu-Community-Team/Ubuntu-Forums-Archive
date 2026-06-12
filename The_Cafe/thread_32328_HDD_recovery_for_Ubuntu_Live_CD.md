---
title: "HDD recovery for Ubuntu Live CD"
date: 2005-05-07
forum: The Cafe
---

### Post by elmimmo on 2005-05-07
Edit: I saw that "Hoary Support > LiveCD was a forum more fit for asking support on this matter. Please accept my excuses.

Please, follow this other thread to answer:
[http://ubuntuforums.org/showthread.php?p=161922#post161922](http://ubuntuforums.org/showthread.php?p=161922#post161922)

---
Hi,

I do not know if this is the proper place to ask for free support, but no other forum seemed more appropriate, so please forgive me if this is not the place.

I have a PC notebook with a seemingly dead hard disk, not backed up, that I would like to try to recover before trying the final format-and-say-bye-bye-to-everything. I still do not know if the error is of data corruption or mechanical malfunction.

I wondered if anyone can think of some sort of an application that does more or less the same things as "Scandisk" or "Norton Disk Doctor" for Windows, that I can use from an Ubuntu Live CD (which I am using right now to plead for help [-o< ).

The added problem is that my only other computer is an iMac G3, so removing the HDD and plugging it onto the other computer is not a possibility.

I tried simply booting with the Live CD, mounting the HDD in order to later on save what could be saved without any recovery method by transfering it through the network to the iMac. But I am quite an ignorant in Linux, and mounting it did not work, so it is not like I can do much more by myself.

In order to mount the disk, which I have no clue wether is FAT32 or NTSC formatted I opened "Root Terminal" from the menu Applications > System . And wrote:```
mkdir /bad-disk
mount /dev/hda1 /bad-disk
```Trying to access that directory afterwards, froze Ubuntu. Rebooting and trying the following ```
mkdir /bad-disk
mount -t ntsf /dev/hda1 /bad-disk
```Reported the following error```
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```and typing "dmesg | tail" reported the following```
mtrr: base(0xb0020000) is not aligned on a size(0x300000) boundary
apm: BIOS not found.
cs: IO port probe 0x0100-0x04ff: excluding 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
NTFS driver 2.1.22 [Flags: R/O MODULE].
NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.
```

I guess the first way to mount it was good enough and that the real problem is that the data is corrupted (to a higher or lower level). But that is just a guess without a knowledgeable base, and anyhow does not help me much in order to be able to try other things.

So, does anyone have any thoughts on what else I could try?

   elmimmo

PS: By the way, I tried to mount /dev/hda1 because that in Device Manager there is a "Volume" listed branching from the "blah blah Ultra ATA controller" with "block.device" parameter set as "Type: string; Value: /dev/hda1". The only other device connected to that controller is a "Slimline DVDRW blah", so I guess that the former Volume refers to the HDD. But, as I said, I am quite an ignorant regarding Linux.

---

### Post by kvidell on 2005-05-07
[QUOTE=man fsck]NAME
       fsck - check and repair a Linux file system

SYNOPSIS
       fsck [ -sAVRTNP ] [ -C [ fd ] ] [ -t fstype ] [filesys ... ] [--] [ fs-specific-options ]

DESCRIPTION
       fsck  is  used  to  check  and optionally repair one or more Linux file systems.  filesys can be a device name (e.g.  /dev/hdc1, /dev/sdb2), a
       mount point (e.g.  /, /usr, /home), or an ext2 label or UUID specifier (e.g.  UUID=8868abf6-88c5-4a83-98b8-bfc24057f7bd or LABEL=root).   Nor&#8208;
       mally,  the fsck program will try to run filesystems on different physical disk drives in parallel to reduce total amount time to check all of
       the filesystems.

       If no filesystems are specified on the command line, and the -A option is  not  specified,  fsck  will  default  to  checking  filesystems  in
       /etc/fstab serial.  This is equivalent to the -As options.

       The exit code returned by fsck is the sum of the following conditions:
            0    - No errors
            1    - File system errors corrected
            2    - System should be rebooted
            4    - File system errors left uncorrected
            8    - Operational error
            16   - Usage or syntax error
            32   - Fsck canceled by user request
            128  - Shared library error
       The exit code returned when multiple file systems are checked is the bit-wise OR of the exit codes for each file system that is checked.

       In  actuality,  fsck is simply a front-end for the various file system checkers (fsck.fstype) available under Linux.  The file system-specific
       checker is searched for in /sbin first, then in /etc/fs and /etc, and finally in the directories listed  in  the  PATH  environment  variable.
       Please see the file system-specific checker manual pages for further details.[/quote]

That's the best I can think of right now.
Best of luck to you!
- Kev

---

### Post by elmimmo on 2005-05-07
Please, forward answers at the thread pointed out at the beginning. (Thanks for that first answer!)

---

