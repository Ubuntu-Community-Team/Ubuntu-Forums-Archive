---
title: "Ubuntu 16.04 Server / grub-install /dev/sda failed"
date: 2017-01-12
forum: Server Platforms
---

### Post by chtsalid on 2017-01-12
Hi all,

I am trying to install the Ubuntu 16.04 Server version on an HP DL360 Gen9 and getting the following message

Executing 'grub-install /dev/sda' failed.

This is a fatal error.

I partitioned the 4 drives as following

Raid 0(100G)->vgsys -> root, var, tmp, swap
Raid 1(890G) ->vgdata -> home
Raid 2(512MB) -> without lvm -> mount /boot

Any idea?

Many thanks!

---

### Post by darkod on 2017-01-12
Do you have msdos or gpt table on sda?

If you have gpt, grub2 needs small 1MiB partition with bios_grub flag on it (no filesystem, do not format it). Without this partition grub2 can't install on gpt disks.

---

### Post by chtsalid on 2017-01-12
Hi,

many thanks for your reply! I think it asks you during the installation whether you want to force the installation with UEFI. I have tried both to force and not force but the result is always the same.

Is this the say to select gtp?

Assumingly that I force the installation with UEFI, in other words gpt, what specificaly should I do in partitioning face?(Please give me more details.)

Many thanks!

---

### Post by darkod on 2017-01-12
I am not sure if selecting UEFI boot makes the disk gpt automatically. The thing is that for windows you need gpt for UEFI boot, but linux can work with UEFI boot and msdos tables... So it is not a requirement the disk to be gpt just because you selected UEFI boot.

Since linux servers work just fine with legacy boot, I am staying away from UEFI boot honestly. So I know very little about it. UEFI has one more partition (EFI boot partition), and that in my opinion is one more complication to manage, so why use it if legacy boot works just fine.

If you want any partition larger than 2TB (2.2TB to be exact) you will need gpt table because msdos can support only up to that size. Your raid arrays in the first post are small, so in theory you don't need gpt and msdos table will do. When you create partition table by default it should create it as msdos. But to be sure you can try the following:
During manual partitioning in the server instaler, position the selection on the disk (for example /dev/sda) and press Enter. That is how you write new partition table in the server installer. It should offer you choice to select partition table type, amond which msdos and gpt...

That way you can be sure of the table type.

Are you using the server raid or linux mdadm software raid? Because you mention only sda but if you use the server raid and have three arrays, all of them will show as separate disks to the OS, so you will have sda-sdc.

And if you have msdos tables on them, you don't need any bios_grub partitions.

Another good option is to use ubuntu desktop live cd on the server first, and do prepared partiitoning in advance. I like that. After that the server installer will detect all partitions and you can use them as necessary. That can also help you to get the partitioning correct in advance.

If you do use gpt tables for any reason, there is also a difference if you use legacy or uefi boot. For legacy boot you only need to make one small 1MiB partition at front, with no filesystem, and with bios_grub flag.
If you use uefi boot, you need the EFI system partition plus the small 1MiB partition. The EFI partition needs to be fat32 I think, around 250-300MiB size. But as I said, I don't work with uefi boot on servers and have no first hand experience...

---

### Post by oldfred on 2017-01-12
If partitioning in advance, you can with gparted select either the default MBR(msdos) or gpt(GUID). 
But that is only for the non-RAID parts of a drive.

What type of RAID?
BIOS or FakeRAID, hardware RAID, or softraid using mdadm?

I know UEFI, but not RAID nor Servers, so Darkod can help more. But he still prefers BIOS boot which is well understood as it has been used for years.

Post this, but it may not show RAID partitions.
 sudo parted /dev/sda unit s print

---

### Post by chtsalid on 2017-01-12
Hi,

thank you for your help guys,

we have 4 drives and use softraid. Actually I configured the raid during the installation process (manual partitioning). I think the HP Server has selected to boot in UEFI in bios settings, maybe I have to change this and configure legacy boot, right?

How can I select MBR during the installation process?

Many thanks!

---

### Post by darkod on 2017-01-12
The way I understand it, the OS installs in the same mode that it is booted as. So if your bios boots the cd/usb stick in uefi, it will try to install ubuntu server in uefi too. Oldfred knows more about this...

So, first thing I would try is to disable uefi boot in bios (if possible). That is of course, if you accept using legacy boot. That way you will be sure the installer is booted in legacy mode.

After that, on the partitioning page creating msdos partition tables is all you need. And by default the installer creates msdos tables.

In such case, grub-install at the end of the installer should not fail.

---

### Post by chtsalid on 2017-01-12
Thank you all for your input, I will try it and let you know!

---

