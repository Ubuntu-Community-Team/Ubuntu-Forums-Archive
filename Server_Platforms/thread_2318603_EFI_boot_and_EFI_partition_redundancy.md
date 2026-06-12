---
title: "EFI boot and EFI partition redundancy"
date: 2016-03-27
forum: Server Platforms
---

### Post by AnrDaemon on 2016-03-27
I've searched across the forums, and found [this interesting topic]("http://ubuntuforums.org/showthread.php?t=2315007"). Not strictly relevant to my question, but provided an interesting insight nonetheless.
While I suppose I can wrest the grub-efi into booting my system even if installation fails, I still have one relevant concern, though.

I have an mdadm RAID1 array set as root partition on my server. Right now it is rather happily booting from any device in the array in legacy mode. Now, I plan to change to 64-bit OS and switch to EFI as well.
How to propagate the contents of /boot/efi onto multiple disks to ensure system boot in case any of the devices fail in the array?

My current thought is to make it RAID1 with some legacy superblock located at the end of the array? Any better ideas?

---

### Post by oldfred on 2016-03-27
One advantage of UEFI is that the boot files are just that, files. And you can copy the ESP - efi system partition and restore it, just by copying, no special install required.
So with RAID, I would expect you can just copy the ESP to all drives.

Note that with UEFI, gpt is the standard partitioning, not the old MBR(msdos). Not sure then how it works with RAID. And it may depend a lot on what type of RAID you have. Since I do not really know RAID and all its various versions and differences, details may vary.

---

### Post by AnrDaemon on 2016-03-27
I do know them, and how EFI generally works, don't worry :)
My question was more like "do people have proven and battle-tested solutions", than "is there any solution at all".
I'm open to suggestions.

---

### Post by oldfred on 2016-03-28
Do not know if any of these links help or not:

 Grub2 that has issues with a (RAID) drive >2TB, use separte /boot folder
grub doesn't boot with efi and md raid root (triaged)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738)
RAID install with efi, need configfile and grub in efi partition.
[http://ubuntuforums.org/showthread.php?t=2190716](http://ubuntuforums.org/showthread.php?t=2190716)
[http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm](http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm)
[http://askubuntu.com/questions/659793/how-can-i-install-ubuntu-14-04-64-bit-desktop-on-a-software-raid-1-dual-uefi-boo](http://askubuntu.com/questions/659793/how-can-i-install-ubuntu-14-04-64-bit-desktop-on-a-software-raid-1-dual-uefi-boo)

---

### Post by AnrDaemon on 2016-03-29
None of them are relevant, they all talk about boot failure after server installation in EFI mode, but none addresses my question in the slightest.

---

### Post by darkod on 2016-03-30
Have you tried any tests in VBox for example? Create the raid1 system and then "remove" one of the disks and see what happens. I haven't used efi at all (with or without mdadm) because legacy boot works just fine so far for everything I needed it. It works with GPT tables as opposed to windows, and unless board manufacturers completely remove legacy boot in the future, I don't see why I would ever need it.

As part of the mdadm maybe the efi files are also copied on all disks, so that in case any fail you can boot from any of the others. I would play little in VBox and test what situation you want to test...

PS. Does the efi partition use some flags (like boot flag)? In such case what about this:
- set up mdadm raid1 for the efi partition too
- set the boot flag on the array, not on the physical partitions
- if the efi files are copied according to boot flag, they will be copied to the raid1 array and be raided, so if the primary disk fails in theory it should keep booting from the secondary

Or alternatively, if the efi partition needs to be mounted as /boot during install, that also solved your dilemma, no? You set /boot to be raid1 array and that's it.

---

### Post by AnrDaemon on 2016-03-30
**darkod**, thanks for the reply.
I haven't tried anything yet, least with virtualbox, which have certain "[issues]("http://anr-daemon.livejournal.com/17857.html")", to put it mildly, with EFI boot.
I want to get rid of Legacy boot because hardware EFI boot is that much faster. (Especially with EFIBOOT project, nullifying the need for GRUB or any other bootloader.)
EFI and flags&#8230; None that I can clearly see.
```
root@daemon-vd2:~# parted -l
Model: ATA VBOX HARDDISK (scsi)
Disk /dev/sda: 10,7GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  345MB   344MB   fat32           EFI   msftdata
 2      345MB   2377MB  2032MB  linux-swap(v1)  swap
 3      2377MB  10,7GB  8340MB  ext4            root
```

This is from my test VM using EFI. "msftdata", as far as my understanding goes, is meant to designate FAT partition.

To the last question, no, I don't think that is an easy way out. Or, at least, it isn't as straightforward as you'd like it to be.
ESP needs to be read by EFI BIOS itself, which only understand FAT32 at most.
That's why my idea currently is to use legacy RAID superblock at the end of the partition. To allow operation of the FS like it is a normal FAT partition with no strings attached.

---

### Post by oldfred on 2016-03-30
With gparted it is the boot flag. With gdisk it is code ef00.
But in actuality the ESP - efi system partition is a long partition type GUID (not the unique partition GUID) and different tools use methods to assign it. If anything gparteds use of boot flag confuses thing as it is not a normal Linux boot partition.

But it sounds like you may be using one of the more advanced ways to directly boot with UEFI and then it may not be just the ESP.

[https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)

---

