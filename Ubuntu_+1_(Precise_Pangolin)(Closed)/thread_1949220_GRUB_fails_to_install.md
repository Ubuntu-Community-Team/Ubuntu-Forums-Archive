---
title: "GRUB fails to install"
date: 2012-03-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Skaperen on 2012-03-29
Installing Xubuntu 12.04 beta1, I get an error that GRUB failed to install.  There is no explanation why.  I finished the install without a bootloader.  Then I boot the DVD again and select try mode for a live DVD system.  Then I mount the partitions I installed to as a tree on /mnt and search for any grub logs.  I don't find any I recognize.  Can someone tell me where to look for any grub error messages that might mean something?

There are lots of files in /mnt/boot and /mnt/boot/grub so I assume the grub package installed OK.  But installing the actual bootloader apparently is what failed, and I can't see any indications of why, except that this curious empty file was present:

-rw-r--r-- 1 root root 0 Mar 29 21:42 /mnt/boot/grub/setup_left_core_image_in_filesystem

And yeah, there is a core image (attached to this post):

-rw-r--r-- 1 root root 25436 Mar 29 21:42 /mnt/boot/grub/core.img

The drive in the test box is only 1TB, but the drive in the intended target machines I'm testing this for have 8TB in a hardware RAID (so it shows up as one big 8TB drive).  So I don't think mere size alone is an issue (if it were, it might fail on the target machine, but should succeed on the test machine).

This is what the disk looks like on the test machine as viewed through the live DVD:

```
root@xubuntu:~# gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 397C956D-A7AD-4EB2-ADCA-629EFFC8964F
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 32109 sectors (15.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            4096          524287   254.0 MiB   0700  feynman-boot
   2          524288         4194303   1.8 GiB     0700  feynman-root
   3         4194304         8388607   2.0 GiB     0700  feynman-var
   4         8388608        33554431   12.0 GiB    0700  feynman-var-log
   5        33554432        52428799   9.0 GiB     0700  feynman-usr
   6        52428800       153092095   48.0 GiB    8200  Linux swap
   7       153092096      1953497087   858.5 GiB   0700  feynman-home
root@xubuntu:~# df
Filesystem     1K-blocks     Used Available Use% Mounted on
/cow             1895920   200788   1695132  11% /
udev             1853476        4   1853472   1% /dev
tmpfs             758372      856    757516   1% /run
/dev/sr0          710956   710956         0 100% /cdrom
/dev/loop0        675456   675456         0 100% /rofs
tmpfs            1895920       20   1895900   1% /tmp
none                5120        4      5116   1% /run/lock
none             1895920       88   1895832   1% /run/shm
/dev/sda2        1831272   307352   1432172  18% /mnt
/dev/sda1         243759    31463    199292  14% /mnt/boot
/dev/sda3        2093160   570988   1417316  29% /mnt/var
/dev/sda4       12540484   317820  11593520   3% /mnt/var/log
/dev/sda5        9406668  1838180   7096632  21% /mnt/usr
/dev/sda7      899297152 13424284 840862744   2% /mnt/home
root@xubuntu:~# 
```Edit1: FYI, I am downloading the non-X Ubuntu 12.04 beta1 amd64 ISO now to give that a try and see if maybe it is an Xubuntu build error.

Edit2: I did capture all files (over 2GB) from the installed system so I can still go back and look at any file anyone can suggest.

Edit3: this is 64-bit

---

### Post by oldfred on 2012-03-29
If gpt are you booting with BIOS or UEFI?

If BIOS you need a tiny bios_grub partition of 1MB for core.img to install to correctly. It can be anywhere on drive.

If UEFI the first partition must be efi.

You normally do not need to have separate partitions for each of the system folders. That may be used on servers. Some RAID or LVM may need a separate /boot but desktops normally do not need that.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using EFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
If a new drive, to be safe, create both of these partitions, in addition to your regular Linux partitions. But the efi partition has to be first. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

---

### Post by Skaperen on 2012-03-29
It's BIOS doing the booting.  The test hardware and the target hardware worked in 10.10 and 11.04 with GPT ... although there were failure cases where the installer would just freeze up have clicking on the choice between Try Ubuntu and Install Ubuntu ... when the disk had 59 partitions (yup, GPT can do that ... but the Ubuntu installer can't).

Partitions were previous allocated with gdisk under and earlier version of Ubuntu that was left over on the machine (I think it was 11.04).  So this is a regression issue.  It only has 7 partitions now, and I have installed it with as many as 10 using GPT.

This is going to be a server on a few bigger machines.  Right now I'm going through the motions on a test machine, and someone else will be doing this on the target machines at the colo facility.  We need to have an X server running on the machine for an application that needs it, but otherwise it is a server.

I previously installed Ubuntu server edition on this test machine with exactly the same partitions, just to get a list of packages it installs by default, so I can construct a list to install onto the Xubuntu system, making an effectively merged desktop+server.  That install worked just fine and GRUB worked.  I then zero'ed the partition contents (but the first 34 sectors and last 33 sectors remained so I could re-use the same partition structure.

That's why I have the partitioning as I do ... it will be a server in a colo facility.  X will be accessed via x11vnc.  We're doing it this way because the other X to vnc methods were too slow (the app needs the speed ... vnc does not).

What do you mean by "BIOS boot partition"?  The one typically mounted at /boot that holds the GRUB files (which I have as partition 1)?

This setup did run with the server edition (grub) and does run with Slackware (but I use syslinux instead of LILO there).  So I know it's not something in this machine's BIOS.  I'm not using EFI.

BTW ....

My attempt to cross check this against plain Ubuntu failed due to bug 939450. Beta2 just showed up, so I will just download that for both and see what happens.  Bug 939450 says a fix is released but I don't know if it's in beta2 or not.

---

### Post by oldfred on 2012-03-29
A bios_grub partition is just a space for grub to store its core.img. Normally in MBR a configured core.img is in the sectors after the MBR which does not exist in gpt.

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.
However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. 

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
sudo parted /dev/sda set <partition_number> bios_grub on

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using EFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
If a new drive, to be safe, create both of these partitions, in addition to your regular Linux partitions. But the efi partition has to be first. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

If you're using EFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-2TB disks, so you may need to use another utility to do the partitioning.

Since I hope to get a new computer soon, I am formating my new SSD with both a efi for future use and a bios_grub for use now. Parted shows the efi as having the boot flag.

```
fred@fred-MavericDT:~$ sudo parted /dev/sde unit s print
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sde: 117231408s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size       File system  Name  Flags
 1      2048s      616447s     614400s    fat32              boot
 2      616448s    618495s     2048s                         bios_grub
 3      618496s    58925055s   58306560s  ext4         04
 4      58925056s  117229567s  58304512s  ext4         10

fred@fred-MavericDT:~$ sudo gdisk -l /dev/sde
GPT fdisk (gdisk) version 0.7.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sde: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 85A657E7-D379-4592-B060-E8EA09953D80
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 3821 sectors (1.9 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  
   2          616448          618495   1024.0 KiB  EF02  
   3          618496        58925055   27.8 GiB    0700  04
   4        58925056       117229567   27.8 GiB    0700  10
fred@fred-MavericDT:~$ 


```I am booting 10.10 with gpt and a bios_grub partition. I have now installed 11.10 and 12.04 on my SSD with a bios_grub partition, but last install is the one booting.

If you want to see where everything is installed including MBR, bios_grub or sectors after MBR in MBR partitioning you can run boot _info script.

The git/testing version has some fixes:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```

---

### Post by Skaperen on 2012-03-30
I'm really not following you at all.

I have never set up a bios_grub flagged partition at all, and things have worked before.  Also, it worked just fine in the server edition.  It successfully put GRUB on whatever sectors it runs from, and it booted up successfully.  So on a desktop (Ubuntu, Kubuntu, or Xubuntu) what is different about GRUB (that I don't see in my current 10.10 Ubuntu desktop which also has GPT.

Here is what I have on my desktop machine:```
lorentz/root /root 7# gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 3907029168 sectors, 1.8 TiB
Disk identifier (GUID): FFE70CDB-BA5E-45E2-8CB6-AC3036F34FB8
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Total free space is 0 sectors (0 bytes)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34            2047   1007.0 KiB  8301  Linux reserved
   2            2048          524287   255.0 MiB   0700  Linux/Windows data
   3          524288         4194303   1.8 GiB     0700  Linux/Windows data
   4         4194304        20971519   8.0 GiB     0700  Linux/Windows data
   5        20971520        37748735   8.0 GiB     0700  Linux/Windows data
   6        37748736        54525951   8.0 GiB     0700  Linux/Windows data
   7        54525952        75497471   10.0 GiB    0700  Linux/Windows data
   8        75497472       100663295   12.0 GiB    8200  Linux swap
   9       100663296      3907028991   1.8 TiB     0700  Linux/Windows data
  10      3907028992      3907029134   71.5 KiB    8301  Linux reserved
lorentz/root /root 8# od -x < /dev/sda1
0000000 0000 0000 0000 0000 0000 0000 0000 0000
*
3736000
lorentz/root /root 9# od -x < /dev/sda10
0000000 0000 0000 0000 0000 0000 0000 0000 0000
*
0217000
lorentz/root /root 10# 
```Note that partitions 1 and 10 are empty on the desktop.  I don't know where GRUB boot-time code is located here, but it obviously is not in sda1 or sda10 since those are all binary zero.  Various servers are similar.  I've assumed that GRUB did a two stage method to embed it in the /boot partition (determined at the time the 440 byte bootstrap is placed into sector 0) like, or similar to, SYSLINUX (which I have a better understanding of than GRUB because I use it on my bootable USB memory stick builds and on my Slackware systems),

Ubuntu 12.04 beta1 server amd64 edition installs fine and boots fine with the exact partition table I tried on the desktop editions.  Is that using GRUB?

I'm downloading beta2 now.  WIll try that in the morning.

---

### Post by Skaperen on 2012-03-30
> **oldfred said:**
> Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

On the issue of separate partitions, the way I have done it (not for dual boot) does vary somewhat from one machine to another.  And I have tried to tend to do it in a consistent way, even if some machines don't need all of the separations.  But that was because of the requirement of MBR logical partitions to not have gaps, and my desire for achieving consistency between machines (never really accomplished).  With GPT, at least the no-gap limitation is gone.  I can just assign whatever number I want, and if a given separate filesystem is not on some system, I leave it out.  Now I need to get back to some consistency and draw up a plan with mount point path to number relationships I can make universal.

One critical thing that I have to separate partitions with is when mount options need to be different.  But also, I sometimes need to prevent some fileystems from overflowing others.  So "everything in one big partition" just doesn't work for me, even on my desktops.  Less critical machines (like my netbooks I hardly ever use) I might do that with.

Now btrfs is changing the game.  It can separate things to have separated using volumes rather than partitions.  At least in most cases.  I can envision a system with one big partition and not even have a separate /boot (at least SYSLINUX supports btrfs ... dunno about GRUB ... and LILO is no longer being considered anymore).

Now back to our regularly scheduled show.

---

### Post by NHclimber on 2012-03-30
> **Skaperen said:**
> I'm really not following you at all.

What else do you expect oldfred to explain to you here?

He's provided an extremely detailed *and accurate* post explaining that GRUB2 + GPT requires a dedicated partition to install its core.img file to.  Even a casual "grub2 gpt" google search drops a half-dozen reputable sources detailing the same information.  For example, from Arch Wiki ([https://wiki.archlinux.org/index.php/GRUB2#GPT_specific_instructions](https://wiki.archlinux.org/index.php/GRUB2#GPT_specific_instructions)):
```

**  Preliminary Requirements for GRUB2 **

 **  BIOS systems **

 **  [GPT]("https://wiki.archlinux.org/index.php/GPT") specific instructions **

 GRUB2 in BIOS-GPT configuration requires a BIOS Boot Partition to embed its core.img  in the absence of post-MBR gap in GPT partitioned systems (which is  taken over by the GPT Primary Header and Primary Partition table). This  partition is used by GRUB2 only in BIOS-GPT setups. No such partition  type exists in case of MBR partitioning (at least not for GRUB2). This  partition is also not required if the system is UEFI based, as no  embedding of bootsectors takes place in that case. Syslinux does not  require this partition. 
For a BIOS-GPT configuration, create a 2 MiB partition using  cgdisk or GNU Parted with no filesystem. The location of the partition  in the partition table does not matter but it should be within the first  2 TiB region of the disk. It is advisable to put it somewhere in the  beginning of the disk before the /boot partition. Set the partition type  to "EF02" in cgdisk or set <BOOT_PART_NUM> bios_grub on in GNU Parted. 
  Note: This partition should be created before grub-install or grub-setup is run or before the Install Bootloader step of the Archlinux installer (if GRUB2 BIOS is selected as bootloader).


```I think you're oversimplying the "things worked before" -- you've never done exactly what you're trying to do here before, otherwise you wouldn't need to compare it with 10.10 or Syslinux or some other different piece of hardware.

> **Skaperen said:**
> Also, it worked just fine in the server edition.   It successfully put GRUB on whatever sectors it runs from, and it booted  up successfully.

Then, install the server edition, and install the desktop packages on top (rather than the other way round).
Or, do all the installation from "what worked before" and upgrade.

Besides, if this is a test run for RAID hardware you should be using the alternate iso and be prepared for bugs there when run on actual RAID hardware.

---

### Post by oldfred on 2012-03-30
I do know the old instructions with gpt said it would install but use blocklists if there was no bios_grub partition. Blocklists are what grub2 uses if you install to a partition in MBR. But blocklists are not recommended and considered unreliable, so maybe they now do not allow the blocklist method? Grub 1.99 has many changes, so maybe it does not work with blocklists anymore.

This is what I got with one of my first grub2 installs which was to a partition.

> Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force 


---

### Post by Skaperen on 2012-03-30
> **NHclimber said:**
> What else do you expect oldfred to explain to you here?
In order to understand why GRUB requires this special partition, I needed to understand why it does NOT actually require it.

Perhaps GRUB itself does not, but the Ubuntu installer scripts ... JUST for desktop, NOT server ... assume that it is provided ... and do so in an UNGRACEFUL way (wrong output, crash, etc).  I suspect this may very well be the case.

Desktop AND server editions prior to 11.10 (I skipped that version) install and boot just fine without the special partition.  Server edition in 12.04 beta1 installs and boots just fine without the special partition.  So I am unable to follow a contrary statement without finding out what is different about the situation.  Maybe what he described did not apply to my case for some reason.  Or maybe what he described only applied to the latest version of GRUB AND the server edition uses an earlier version.  Maybe the server install scripts are not as presumptuous as the desktop install scripts (plausible because desktops up until just lat last year when 3Tb drives showed up were typically not seeing any hard drive that needed GPT and so bug testing of the desktop install scripts in this scenario was much less).

> **NHclimber said:**
> He's provided an extremely detailed *and accurate* post explaining that GRUB2 + GPT requires a dedicated partition to install its core.img file to.  Even a casual "grub2 gpt" google search drops a half-dozen reputable sources detailing the same information.  For example, from 

Although I have not yet had the time to do a full research on THIS new (to me) situation, I can say that very typically lots of documentation describes situations that don't always apply to everyone.  And often, they are "blown out of proportion" by writers with agenda (e.g. "it's required" when reality is "it's urged").  One thing is for sure the same: I did not provide a "boot loader" partition identified as such.  I have in the past provided some reserved space in case that might be needed.  But not always.  And when I did nothing ever physically tried to use it (it always remained binary zero).

> **NHclimber said:**
> Arch Wiki ([https://wiki.archlinux.org/index.php/GRUB2#GPT_specific_instructions](https://wiki.archlinux.org/index.php/GRUB2#GPT_specific_instructions)):
```

**  Preliminary Requirements for GRUB2 **

 **  BIOS systems **

 **  [GPT]("https://wiki.archlinux.org/index.php/GPT") specific instructions **

 GRUB2 in BIOS-GPT configuration requires a BIOS Boot Partition to embed its core.img  in the absence of post-MBR gap in GPT partitioned systems (which is  taken over by the GPT Primary Header and Primary Partition table). This  partition is used by GRUB2 only in BIOS-GPT setups. No such partition  type exists in case of MBR partitioning (at least not for GRUB2). This  partition is also not required if the system is UEFI based, as no  embedding of bootsectors takes place in that case. Syslinux does not  require this partition.
For a BIOS-GPT configuration, create a 2 MiB partition using  cgdisk or GNU Parted with no filesystem. The location of the partition  in the partition table does not matter but it should be within the first  2 TiB region of the disk. It is advisable to put it somewhere in the  beginning of the disk before the /boot partition. Set the partition type  to "EF02" in cgdisk or set <BOOT_PART_NUM> bios_grub on in GNU Parted. 
  Note: This partition should be created before grub-install or grub-setup is run or before the Install Bootloader step of the Archlinux installer (if GRUB2 BIOS is selected as bootloader).


```I think you're oversimplying the "things worked before" -- you've never done exactly what you're trying to do here before, otherwise you wouldn't need to compare it with 10.10 or Syslinux or some other different piece of hardware.
How is it that I have "never done ... trying to do here before".  As far as I consider it, I'm doing the same KIND of thing.  The partition numbers are a bit different but if that matters, it really is strange.  Of course, one difference is I'm installing Xubuntu 12.04 beta1 instead of Ubuntu server 11.04.  If that matters, it should be said.  Does it?

> **NHclimber said:**
> Then, install the server edition, and install the desktop packages on top (rather than the other way round).
Or, do all the installation from "what worked before" and upgrade.
When the final target will be installed, there will be no one present at the console during the addition of more packages.  I believe the X packages will stop and wait for the expected user at the console to respond with a test of the X server so it can configure the X configuration for that video card and the monitor's dimensions.

At run time, access to that X server will be exclusively via VNC.  We already tried software based Xvnc programs (found 2 of them) and they were annoyingly slow to run the apps on (even with a VNC session not connected, which should thus never block for a VNC transmission).  X11vnc is supposed to let VNC have access to an existing hardware based X server.  It is believed that will run faster (perhaps because "blit and pixel" operations are done in video card acceleration faster than in CPU on a buffer, and transfer back to the CPU would only be needed for the end results when VNC needs it).

> **NHclimber said:**
> Besides, if this is a test run for RAID hardware you should be using the alternate iso and be prepared for bugs there when run on actual RAID hardware.I don't see why the alternate install applies here.  Again, this is a case of "it works before" which needs an assertion of "well they changed this at this version".  Yes, I have installed desktop versions of Ubuntu onto server hardware with hardware RAID before and did not have any issues (aside from the issues that pre-existed that prompted me to do that install to help diagnose what was going on).

---

### Post by Skaperen on 2012-03-30
> **oldfred said:**
> I do know the old instructions with gpt said it would install but use blocklists if there was no bios_grub partition. Blocklists are what grub2 uses if you install to a partition in MBR. But blocklists are not recommended and considered unreliable, so maybe they now do not allow the blocklist method? Grub 1.99 has many changes, so maybe it does not work with blocklists anymore.

This is what I got with one of my first grub2 installs which was to a partition.

OK, this now means something to me.  It explains how it has been working succesfully on GPT partition tables up to this point.  Your speculation that it has changed behavior in the version used in Ubuntu 12.04 is very plausible.  And maybe they even announced it to those watching GRUB development.  Maybe Ubuntu should have done similar, or at least reworded messages to say that GRUB **NOW** requires this partition in all cases of GPT (or similar for cases where the MBR layout doesn't provide enough space from sector 1 onward).

Either server edition uses an older GRUB (where the requirement is not enforced), or the scripts in the desktop edition are presumptuous and ungraceful.  Or buggy.

But at least I'm better understanding what is going on enough to move on ...

Your example showed some flag named "bios grub".  Is that really a different partition type code?  Is type code EF02 sufficient to mark a partition for this purpose?  Is it OK to start this partition at sector 34 or is it better to start it at a high level alignment?  I now do alignments at 2M based on some reported changes about how Linux caches buffers.  I could put this in the upper half of the first 2M of the disk if a 1M alignment is useful (hopefully 1M of space is sufficient for GRUB in the foreseeable future).

But I will still be using gdisk for setting up partitions because it has a straightforward command syntax I can generate from my scripts that calculate partitions for me.  I did try parted about 3 years ago and it just messes up stuff (changed partition numbers, mostly, and sometimes changed start sectors).  I'm done with parted.

Is there any partition number requirement for the boot loader partition?  I don't want to change my existing partition number models.  Could it use partition number 100 for example?

---

### Post by Skaperen on 2012-03-30
Your quote did not show up as a subquote.  So I'll just refer back to it.  This post is just a sidetrack curiosity.  If GRUB should not be installed in a partition, I wonder if Windows might have the same issue leading them to require a UEFI boot process when GPT is used (e.g. with a BIOS machine you cannot use GPT in Windows) because they just didn't want to set up a bootloader partition.

---

### Post by oldfred on 2012-03-30
Windows does require a efi partition if the drive is gpt and you are booting with UEFI. And the efi partition for everyone must be the first partition. But Windows will not boot from gpt with BIOS where Ubuntu will. Windows will read data from gpt partitions as long as it boots from another drive with MBR in BIOS.

While the efi partition has to be first the bios_grub can be anywhere on drive or last partition if you want the bios_grub flag in gparted or EF02 setting in gdisk is all that is required. So partition 100 is ok. (have not tried it).

Since I hope to get a new UEFI system this year, my new SSD has space for both efi & bios_grub. With my current BIOS I am using bios_grub and will use efi in the new system.

Partitions should start with sectors that are divisible by 8. Most default to first partition starting at 2048 now.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

### Post by Skaperen on 2012-03-30
What does "first partition" mean?  Is it partition number 1?  Is it the lowest numbered existing partition?  Is it a partition at a start specific sector?  Is it the partition with the lowest start sector?

This ambiguity exists because GPT does allow partition numbers to be in a different order than their start sectors.  If partition 1 begins at sector 33554432 and partition 2 begins at sector 2097152, which is "first".

**Abbott:** You load the bootloader to first sector.
**Costello:** Then how is it loaded?
**Abbott:** Naturally.
**Costello:** Naturally.
**Abbott:** Now you've got it .
**Costello:** I load the loader Naturally.
**Abbott:** You don't! You load to Where?
**Costello:** Naturally.
**Abbott:** Well, that's it—say it that way.
**Costello:** That's what I said.
**Abbott:** You did not.
**Costello:** I said I load the bootloader on Naturally.
**Abbott:** You don't! You load it on Who!
**Costello:** Naturally.

My post about Windows was less about their technology and more about what they chose not to do.  In particular, their bootloader is NOT in a regular partition under GPT as it can be in MBR.  The usual way to multiboot with Windows is to chain load the Windows bootloader from its partition.  I'm more curious why they did not support BIOS booting a GPT even though Linux can (with GRUB, either with the discouraged blocklist, or with the preferred EF02 sector).  I might like to claim that did so just to frustrate dual booting with Linux.  But I really don't know why.  It could just be that they didn't think that the 2TB line would be breached before UEFI was common (well, it was).

---

### Post by Skaperen on 2012-03-30
As for alignment, check out the numbers I posted.  All but the first two partitions are on exact 1GB boundaries.  The 2nd (/) is on a 256MB boundary, and the 1st (/boot) is on a 2MB boundary.

I've been doing 1MB boundaries since 1999, and stepped up to 2MB boundaries when I read a ChangeLog entry for the kernel mentioning some caching sizing increased to 2MB.

I have in the past sometimes placed a partition over the gap from sector 34 to 4095.  I just marked it "8301 Linux Reserved".  So I guess what I need to do now is go back to that consistently and mark it "ef02 BIOS boot partition".

It has to be below the 2TB line for what reason ... because BIOS can't go beyond there?  Or because the BIOS real mode API has no means to express a point beyond there?

Does GRUB even need a separate /boot if it uses the EF02 partition for its image ... assuming the partition where it does read files from is under the 2TB line?  Can I just merge /boot and / together (/home will be the only partition going out over the 2TB edge)?

---

### Post by oldfred on 2012-03-30
The efi partition does not have the boot files as I understand it. 

Someone posted this as in the efi partition:

/boot/efi/EFI/ubuntu/grubx64.efi

If you are booting RAID, LVM, with encryption or some of the newer formats you may need a separate /boot otherwise I do not think so.

---

### Post by Skaperen on 2012-03-31
Here's the new plan. Units are 512 byte sectors.  Any comments?

```
part---------start-----------end----------size
   0             0             0             1  ---- MBR boot sector and legacy table
   0             1            33            33  ---- Partition table primary
 127            34          2047          2014  8301 Linux reserved
 120          2048          4095          2048  EF02 BIOS boot sector
   1          4096        524287        520192  8300 Linux - /boot        ext2    rw,noatime,nodev,nosuid,sync
   2        524288       4194303       3670016  8300 Linux - /            ext2    rw,noatime
   3       4194304       5242879       1048576  8300 Linux - /var         ext4    rw,noatime,sync
   4       5242880      11534335       6291456  8300 Linux - /var/log     ext4    rw,noatime,nodev,nosuid,noexec
   5      11534336      16252927       4718592  8300 Linux - /usr         ext4    rw,noatime
   6      16252928      41418751      25165824  8200 Linux swap           swap
   7      41418752    7812415487    7770996736  8300 Linux - /home        ext4    rw,noatime,nodev
 128    7812415488    7812456415         40928  8301 Linux Reserved
   0    7812456416    7812456447            33  ---- Partition table secondary
part---------start-----------end----------size
```

---

### Post by effenberg0x0 on 2012-03-31
@oldfred 

Your posts in this thread cleared up two doubts I had about gpt, so Thank you :)

Regards,
Effenberg

---

### Post by oldfred on 2012-03-31
@Skaperen
Do not know enough to see any issues. Everyone has there own preferences as to 'best' partitioning and layout looks ok to me.

@Effenberg
What little I know about gpt was from srs5694 when he was posting here. Early on he would often correct me (or more fully explain). His site is still the best resource for info (rodsbooks.com).

---

### Post by Skaperen on 2012-03-31
I'm sure there are often many differences in usage that no one layout is optimal for all.  And people who just do one big single partition for everything still have the "it works" experience.  And more often, people just let Ubuntu set up the partitions, especially for desktops.  I would assume that part is better tested.

So, if nothing stands out as unworkable with that layout, I'll give that a try tonight.

---

### Post by Skaperen on 2012-04-01
The layout was changed (due to other errors) to:
```
part---------start-----------end----------size
   0             0             0             1  ---- MBR boot sector and table
   0             1            33            33  ---- Partition table primary
 127            34          2047          2014  8301 Linux reserved
 120          2048          4095          2048  EF02 BIOS boot sector
   1          4096        262143        258048  8300 Linux - /boot        ext2    rw,noatime,nodev,nosuid,sync
   2        262144       2097151       1835008  8300 Linux - /            ext2    rw,noatime
   3       2097152       6291455       4194304  8300 Linux - /var         ext4    rw,noatime,sync
   4       6291456      31457279      25165824  8300 Linux - /var/log     ext4    rw,noatime,nodev,nosuid,noexec
   5      31457280      50331647      18874368  8300 Linux - /usr         ext4    rw,noatime
   6      50331648     150994943     100663296  8200 Linux swap           swap
   7     150994944    1953497087    1802502144  8300 Linux - /home        ext4    rw,noatime,nodev
 128    1953497088    1953525134         28048  8301 Linux Reserved
   0    1953525135    1953525167            33  ---- Partition table secondary
part---------start-----------end----------size
```and it installed just fine and boots up and runs.

---

### Post by oldfred on 2012-04-01
Glad you got it working.

I did see where someone posted a bug that partition 27 would not work correctly. It became sdaa in some places but not others. So while gpt allows 128 partitions, sda thru sdz seems to be the current limit. I think this total number of created partitions and not a partition number in gpt.

---

### Post by Skaperen on 2012-04-01
> **oldfred said:**
> Glad you got it working.

I did see where someone posted a bug that partition 27 would not work correctly. It became sdaa in some places but not others. So while gpt allows 128 partitions, sda thru sdz seems to be the current limit. I think this total number of created partitions and not a partition number in gpt.

Partition 27 should be sda27, or sdb27, sdaa27, sdab27, etc.  Do you mean 27 disks?  Or does something in ubuntu installer confuse partitions with disks?

I do know one disk with 59 partitions (with gaps in the numbering) froze the installer from 9.10 through 11.04.  It froze before presenting the screen that gave me the option to manually configure the partitions.  OTOH, the install I just did had gaps from 7 to 120 and from 120 to 127, so I don't think gaps is an issue or if it was, they have fixed it.  I'll try to run the installer with those partitions sometime when I get a chance.

---

### Post by oldfred on 2012-04-02
You may be correct, it was not partitions but drives that the issues was with. I think I mixed it up but do not have a reference to go back and find.

---

