---
title: "How to install Ubuntu 16.04 with btrfs on a DELL PowerEdge T330?"
date: 2016-10-18
forum: Server Platforms
---

### Post by ubudabi on 2016-10-18
Hi all,
I have a new **DELL PowerEdge T330** which is certified for Ubuntu 14.04 and has similar specifications like the one here:
[https://certification.ubuntu.com/hardware/201603-21234/](https://certification.ubuntu.com/hardware/201603-21234/)

The server was delivered with a 1 TB hard disk and I can see 2 partitions on it with GParted:
sda1: Volume Label: -, FS: FAT16, Capacity:39.2 MB
sda2: Volume Label: OS, FS: FAT32, Capacity:2GB
the rest space is unallocated.
My intention is to create with GParted 2 new partitions for root and swap using the free space, format the root partition with **btrfs **and install Ubuntu 16.04 x64 Desktop on it. I also have 6 HDDs with which I want to build a ZFS RAID later.
The issue is I am not sure how to proceed since I am not familiar neither with such servers nor with btrfs, so my questions concern both.
**PowerEdge **has this **Lifecycle Controller **function which can be used to install OSes. On the list of OSes Red Hat, SuSe and Windows are included but not Ubuntu although certified. According to the video here:
[http://www.dell.com/support/contents/ch/de/chbsdt1/videos/videoPlayer/5taTZzdjpq6sPmi516sgAu8krVzac6Kj](http://www.dell.com/support/contents/ch/de/chbsdt1/videos/videoPlayer/5taTZzdjpq6sPmi516sgAu8krVzac6Kj)
"The system loads relevant drivers for the selected OS".

1. So, what is with Ubuntu? Are drivers missing or is there any disadvantage in general in comparison to Red Hat, SuSe or their derivatives?
2. Can or should I use the **Lifecycle Controller and choose **"Any Other Operating System" to install Ubuntu or should I just delete all partitions and install Ubuntu the normal way?
3. My HDDs are 4 TB each. Am I OK if leave the BIOS option like it is before the installation?
4. How should I configure the partitions with GParted or the installer? The SuSe installer configures the btrfs subvolumes other than the Ubuntu installer:
[https://www.suse.com/documentation/sles-12/stor_admin/data/sec_filesystems_major.html](https://www.suse.com/documentation/sles-12/stor_admin/data/sec_filesystems_major.html)
Can the Ubuntu installer be configured to create other subvolumes? Would I still be able to use **snapper **if leave it like it is? (I have already installed Ubuntu 16.04 on my desktop but I am not able to use **snapper**. I assume I have managed  to miss-configure my partitions).
5. Where should GRUB be installed? On sda, or on root or somewhere else?

Any advice?
Thanks in advance!

---

### Post by oldfred on 2016-10-18
Moved to Server Sub-Forum where those who may know your type of issues can help.
I do not know BTRFS, but have seen some issues.

If not familiar with BTRFS why do you want it?
Often better to stay with standard ext4 at least for / (root).

Btrfs RAID 5/6 Code Found To Be Very Unsafe & Will Likely Require A Rewrite
[https://www.phoronix.com/scan.php?page=news_item&px=Btrfs-RAID-56-Is-Bad](https://www.phoronix.com/scan.php?page=news_item&px=Btrfs-RAID-56-Is-Bad)

 Linux 4.7 - Btrfs vs. EXT4 vs. F2FS vs. XFS vs. NTFS Benchmarks
[https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.7-FS-5-Way](https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.7-FS-5-Way)
6-Way File-System Comparison On The Linux 4.1 Kernel
[http://www.phoronix.com/scan.php?page=article&item=linux-41-filesystem&num=1](http://www.phoronix.com/scan.php?page=article&item=linux-41-filesystem&num=1)

With UEFI and gpt partitioning, you always install grub to a drive, but with UEFI, Ubuntu's grub only installs to the ESP - efi system partition on sda.

---

### Post by ubudabi on 2016-10-18
[COLOR=#000000]@oldfred: thanks for the quick response and your advice! 

Could someone with a PowerEdge server give more tips?[/COLOR]

---

### Post by darkod on 2016-10-18
I can help to answer few of the questions. Some of it are things you need to decide...

1-2. I wouldn't rely on any Lifecycle Controller. Simply install the ubuntu server OS and remove any existing partitions, unless you need some of them for UEFI boot. This is related to point 3 too.
3. The BIOS option I would change is disable UEFI boot if possible. That should make the server and the ubuntu installer to boot in legacy mode, which I always prefer over UEFI. But you might have another opinion. The difference between legacy boot and UEFI boot is also in which partitions you will need on the OS disk.
4. How you decide to do partitioning depends on your needs. Usually the installer can do any partitioning layout you desire (mdadm raid, LVM, encryption, etc). But I have never installed btrfs yet, so I can't comment if that option is fully supported during install. I would say yes...
5. GRUB is bootloader and always goes to the MBR of the disk (like /dev/sda). Never on a partition (like the root partition). The boot process begins with the disks MBR and if the bootloader is on a partition it usually can't be found.

---

### Post by ubudabi on 2016-10-18
@darkod: thanks for the response and your tips! Yes, I could try to delete all existing partitions and do a clean install. I have backed up these several times in case something goes wrong. But this is not my first choice without knowing what these partitions contain. There are several things which I have encountered for the first time and I try to be cautious. Maybe the [COLOR=#000000]Lifecycle Controller is also involved in the bootloading process. I have no idea...
[/COLOR]

---

### Post by oldfred on 2016-10-18
Typically the FAT16 formatting is not used anymore, not sure why Dell would have that.

And FAT32 now is used with UEFI as the ESP - efi system partition, but very old systems would use it for XP or DOS booting. Newer XP used NTFS.

Darkod knows servers a lot more, but for desktops UEFI is pretty standard. And there is some advantages to gpt partitioning. 
Is you drive gpt or MBR partitioned. Gparted does not seem to tell.
This will show dos (msdos or MBR) or gpt.
sudo parted -l

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help) 

Not sure if all of above applies as well to servers.
But with all my new drives I only use gpt, and include both an ESP - efi system partition for UEFI boot and a bios_grub partition for BIOS boot. Then I can use either one without having to totally redo disk as ESP should be first or near beginning of drive.
Gpt is also now required for all drives over 2TB.

---

### Post by darkod on 2016-10-19
I agree, the FAT16 is probably some Dell tools. The FAT32 is probably the ESP efi partition.

Like oldfred suggests, you can have both the EFI and bios_grub partitions on your OS disk, that way you are prepared to boot both UEFI and legacy.

Your 4TB data disks have to have gpt table but your 1TB OS disk can have msdos and that might be better in this situation, especially if you want to use legacy boot.

What recently happened to me on NUC6 barebone is that I was telling it to use legacy boot (disabled UEFI boot completely) and had gpt table on the SSD, but for some reason the device didn't like that and wasn't booting at all. After banging my head little while, I tried using msdos table and it worked right away. So, even thought I was using only ubuntu (no windows at all on that NUC6) and ubuntu can work with legacy boot and gpt, the device itself didn't seem to like that combination.

In your case if you use gpt table on the OS disk and try legacy boot I'm not sure how it will react.

---

### Post by mastablasta on 2016-10-19
> **oldfred said:**
> 
If not familiar with BTRFS why do you want it?
Often better to stay with standard ext4 at least for / (root).
.

BTRFS is used for data backups and for safer data keeping. the system is more advanced than ext4. it enables data snapshots to be made among other things. kind of like ZFS. it is considered stable and is likely to replace ext4 in the future as standard. and i think in OpenSUSE (or is it just their server variant) BTRFS is already standard.

[URL="https://en.wikipedia.org/wiki/Btrfs"]https://en.wikipedia.org/wiki/Btrfs
[/URL]

---

### Post by ubudabi on 2016-10-19
@oldfred: > [COLOR=#000000]But with all my new drives I only use gpt, and include both an ESP - efi system partition for UEFI boot and a bios_grub partition for BIOS boot. Then I can use either one without having to totally redo disk as ESP should be first or near beginning of drive.[/COLOR]

Good idea!

@oldfred,darkod:
> [COLOR=#000000]Is you drive gpt or MBR partitioned[/COLOR]
> [COLOR=#000000]I agree, the FAT16 is probably some Dell tools. The FAT32 is probably the ESP efi partition.[/COLOR]

With another tool I see this:
- MBR: 0.5 Kb
- fisrt sectors: 31.5 Kb
- MBR partition table: 0.5 Kb
- Unknown: 39.19 Mb, DellUtility
- FAT32: 2048 Mb, OS

So, If I understand correctly it has both MBR and EFI partition? Apparently darkod is right about the Dell tools. 

[COLOR=#000000]@mastablasta: Yes, I also see it like this.

I think I'll try first to install Ubuntu using the [/COLOR][COLOR=#000000]Lifecycle Controller leaving all existing partitions like they are. If there is an issue I'll try without [/COLOR][COLOR=#000000]Lifecycle Controller leaving again all [/COLOR][COLOR=#000000]existing partitions intact and if that doesn't work I'll delete all partitions and install Ubuntu normally.

----------------------------------------------------------------------------------------------
[EDIT]
I have finally installed Ubuntu on my PowerEdge manually. The way via the [/COLOR][COLOR=#000000]Lifecycle Controller didn't work - it was complaining about a missing licence for iDRAC. The installation succeeded without any issues. I have left the existing partitions like they were and created in addition a /boot (ext4), a root (btrfs) and a swap partition. The system seems to be working normally.[/COLOR][COLOR=#000000]

[/COLOR]

---

