---
title: "Sanity check on raid/zfs use, ubuntu with ZFS for backup NAS config"
date: 2016-09-07
forum: Server Platforms
---

### Post by linwood2 on 2016-09-07
Been using ubuntu for a while, but not zfs.  If someone has a few minutes I would appreciate a sanity check for a home backup nas server.  Reliability and stability is the general goal, in particular over time as software is changed; performance not so important as it's only for periodic backups, staging storage, etc.

Not asking so much about specific hardware as it's a recycled workstation, but for context: two of 830 Samsung 256G SSD drives, 4 of 2TB WD HDD's, Intel Z77 chipset and I7-3770k, 32GB ram, headless.

Some specific questions: 

1) It appears it is possible to run ubuntu from a zfs system volume, but it seems a bit more trouble than it is worth, and I planned to do a regular software mirror.  Reasonable?

2) It appears grub is not happy booting in a software mirror partition, so I was going to mirror /, swap, and maybe a zil area, and install grub in a small partition for booting on each SSD.  Is that the most straightforward approach? 

3) The four HDD's were going to be one RaidZ-1 pool.  Yes, some risk of a double failure, but this is one of 4 backups I use (just the most regular) and risk from other corruption sources is probably at least as high as a double failure in rebuild timeframe.

4) I was going to reserve 50G or so on the SSD volume as a software raid 1 device that I will use as a zil cache.  I really doubt I need the performance, but since this is also a learning mode...   Is mirroring this at the software level the right approach?   As just a partition on the SSD? 

Motherboard has AHCI on, raid off, all drives are on intel sata ports.

The real question in all this is whether I've made the right choices of redundancy for different pieces -- none for boot partition, software raid for root, swap and zil, and zfs for the hdd pool? 
BY the way, I've been testing this in Hyper-V before putting on real hardware, and it does seem to work (it's there I learned software raid for the UEFI partition just did not seem to work, for example).  But like so many things, knowing it works does not mean it is a good idea. :confused:

---

### Post by darkod on 2016-09-08
One question: Is EFI boot important for you to use? I guess that is also related to point 2 above because otherwise I don't understand the question in point 2. Legacy grub is on the MBR of the disks and does not mind at all whether you use software raid or not. The only difference is if you are using the older type of msdos partition tables on the disks or gpt tables. With gpt table grub2 needs a small 1MiB partition at front with NO filesystem. This is because gpt MBR is smaller and grub2 doesn't fit on it like on msdos MBR.

If you can avoid using EFI boot i would do that. Besides it's fairly new and if there is no need to use it on production systems, I wouldn't. If I'm not mistaken, whether ubuntu (and grub) install in legacy or EFI boot depends how you boot the install media. If you boot it in legacy, it will be legacy.

I have it like that on my dual boot desktop with a board that is UEFI. But using simple legacy boot. No need to complicate my life... :)

As for the other points:
1. Very reasonable. Although a 256GB SSDs are way overkill if you only plan to put them in SW raid1 and be the OS device. Get any simple cheap HDDs and use the SSDs in a better way. You could even install it on Compact Flash memory cards with CF-to-SATA adapters.

3. There is no question I see here. Raid-z1 is OK for 4 disks, it would be too much waste of space to use raid-z2. If you had for example 6 disks, that would be another story.

4. A ZIL could be a good use of the SSDs (otherwise it's a waste like I commented above). I haven't actually played too much with ZFS and never set up ZIL device, but I would say it uses the partitions directly, not as mdadm array. Need to investigate that more...

---

### Post by linwood2 on 2016-09-08
> **darkod said:**
> One question: Is EFI boot important for you to use? I guess that is also related to point 2 above because otherwise I don't understand the question in point 2. Legacy grub is on the MBR of the disks and does not mind at all whether you use software raid or not. The only difference is if you are using the older type of msdos partition tables on the disks or gpt tables. With gpt table grub2 needs a small 1MiB partition at front with NO filesystem. This is because gpt MBR is smaller and grub2 doesn't fit on it like on msdos MBR.

If you can avoid using EFI boot i would do that. Besides it's fairly new and if there is no need to use it on production systems, I wouldn't. If I'm not mistaken, whether ubuntu (and grub) install in legacy or EFI boot depends how you boot the install media. If you boot it in legacy, it will be legacy.

I have it like that on my dual boot desktop with a board that is UEFI. But using simple legacy boot. No need to complicate my life... :)


That's a very good question.  I started testing this in HyperV and had all sorts of issues that at first I Thought was related to the 1st vs 2nd generation HyperV setup.  In generation one, you could only use simulated IDE drives to boot from, and as I was trying to create mirrored boot volumes, I kept getting stuck where it would not see the boot device.  I thought it was related to bios, and switched to generation 2 which can only do uefi, but will boot from scsi style devices.  My problems changed, and guess I mentally thought I got past an issue, but in reality I think I was still doing the partitioning wrongly.  But I stuck with UEFI in testing and carried it over.

That 1MB block may be what I was missing though in all of that.  I found forum posts indicating it was partition ordering that caused issues, as well as a ton of other advice, none of which worked.  Most of the walk-through's were older ubuntu versions and did not look the same, but in thinking about it, that may have been driven by the UEFI aspect as well (as I chose that in install also). 

Where I got lost as well as I really do not understand the relationship between software raid, and the boot process - can the boot area be in a mdadm raid set?  

> **darkod said:**
> 
As for the other points:
1. Very reasonable. Although a 256GB SSDs are way overkill if you only plan to put them in SW raid1 and be the OS device. Get any simple cheap HDDs and use the SSDs in a better way. You could even install it on Compact Flash memory cards with CF-to-SATA adapters.

3. There is no question I see here. Raid-z1 is OK for 4 disks, it would be too much waste of space to use raid-z2. If you had for example 6 disks, that would be another story.

4. A ZIL could be a good use of the SSDs (otherwise it's a waste like I commented above). I haven't actually played too much with ZFS and never set up ZIL device, but I would say it uses the partitions directly, not as mdadm array. Need to investigate that more...

The hardware is what I had left over from a 4-5 year old workstation, so it is what it is.  I plan to use it just as a nas for backups (not live use), so not sure I have better use for the hardware (and my new workstation has bright shiny new faster SSD's -- finally built one with no spinning disks at all). 

Anyway... 

The Raid-Z1 question indeed was more of a statement; I know some people object to going zfs route without accompanying ECC memory, higher degrees of redundancy, and carry an umbrella all the time in case the roof leaks.  Just wanted to get it said and move on.

ZIL ended up, in testing, being moot.  I'm doing backups to the resulting system and have tried a couple of protocols and programs, and all appear to be doing async writes, which doesn't use the ZIL drive.  But I seem write-speed limited not by the drives, anyway, but by the NIC (at least in the best program).  And I can't team the NICs on the window's box the data originates from (intel vs microsoft spitting match) so trying to speed it up is moot.

Incidentally, Goodsync is the software I think I will use for backups here.  It has a linux server component, which can do an independent read-after-write MD5 checksum, as well as a separate checksum compare later if you want.  Just to find issues that may come from failures in the pipeline.  It can also easily do 1GB speeds continually while doing the comparison (at least with medium size files like I mostly have, photos). 

I think I need to go back and understand the unix boot process, grub/2, etc. much better.  That's where I got totally confused.  Once booted, everything was easy.

Thank you darkod for taking the time to respond.

---

### Post by darkod on 2016-09-08
Yes, the boot area can be in mdadm raid1. It can't be in raid0 for the obvious reason that it splits the files in half and boot files won't tolerate that. I'm not sure about raid5, never tried it. But for raid1, no problems. Both options work, having boot as a folder in / or having a separate /boot (separate mdadm array for it).

The 1MiB partition I mentioned is relevant only for legacy boot and on gpt disks. I'm not aware it is needed for EFI boot. What is needed for EFI boot on the other hand, is a little bigger partition (not sure of recommended size, maybe 200-300MiB) and with FAT32 filesystem if I'm not mistaken. I don't know if that can be on mdadm device, never tried EFI as I mentioned...

---

### Post by linwood2 on 2016-09-08
I'll give it another go in simulation first.  I had a large area (I was using 1G), but I may have gotten things twisted around between UEFI and legacy as I was switching hyper-v generations.  THe core problem that was visible was I either never was able to mark the partition bootable (I assume it's the raid partition), or (and maybe because of) the install couldn't write grub to it.

---

### Post by darkod on 2016-09-08
If you were installing in EFI mode, and using manual partitioning, and didn't create the EFI partition, then grub install will fail. In EFI it needs the EFI partition, just like windows does. That much of EFI I know... :)

And manual partitioning is for your total control, so the installer does not create any partitions for you, including for the bootloader. That might have been why it failed.

---

### Post by linwood2 on 2016-09-09
> **darkod said:**
> If you were installing in EFI mode, and using manual partitioning, and didn't create the EFI partition, then grub install will fail. In EFI it needs the EFI partition, just like windows does. That much of EFI I know... :)

And manual partitioning is for your total control, so the installer does not create any partitions for you, including for the bootloader. That might have been why it failed.

Well, this may be a hyper-v thing, but I tried this again very carefully and did this: 

Created two 50GB drives
Ran 16.04.01 install from virtual DVD
Told it I wanted to be in uefi mode only when it asked
Partitioned both 50GB drives as: [INDENT]1MB marked unused
500MB marked as physical raid (for boot)
10GB as physical raid  (for swap) 
balance as physical raid (for root)[/INDENT]

Of note, it automatically added a 1MB additional area at the beginning, so it went 1MB, 1MB, 500MB, 10GB, balance.

I then created three raid-1 volumes in order: 

[INDENT]2 x 40GB as EXT4 as /
2 x 10GB as swap 
**2 x 500MB as EFI partition (it automatically marked it bootable)**

[/INDENT]
I let it continue the install, and it gave no errors.

Upon attempting to boot HyperV lists each disk and says "No UEFI-compatible file system was found". 

This is what I got before (when I did not insert that extra 1MB area). 

I do not really care if it works in Hyper-V, but wanted to see this work before I tried redoing the physical hardware.  So either Hyper-V won't work in this way, or I am doing something wrong.

In particular, is the part in bold above correct, that the EFI partition can be on a Raid-1 software raid volume?   If the above approach is OK, then I assume this is Hyper-V weirdness.  

I think I am a bit down a rat hole with regard to the original question, though I do need to come back to that.  I accidentally did a "test" of the boot on what I did in physical hardware (where the EFI partition was not raid) -- In cleaning up cabling I unplugged the power to one drive and did not notice.  It was one of the two boot drives.  The system would not boot.  Which is bad (though easily fixable even if it failed, from a bootable USB or DVD I think).   So I am now off to read about GRUB2 and see if it should be manually installed in two places (or maybe it already is), or something else.

Linwood

PS. Secure Boot was disabled.

---

### Post by bob_jones2 on 2016-09-09
[I]this may be a hyper-v thing


[/I]@linwood2Not saying you would personally do it, but just thought it ought to be put on record for anyone reading this forum....

_Never, ever, use ZFS with abstraction layers (be it virtualization or RAID controllers)_[I]_._
[/I]

---

### Post by linwood2 on 2016-09-09
> **bob_jones2 said:**
> [I]this may be a hyper-v thing


[/I]@linwood2Not saying you would personally do it, but just thought it ought to be put on record for anyone reading this forum....

_Never, ever, use ZFS with abstraction layers (be it virtualization or RAID controllers)_[I]_._
[/I]
Yes, this was just for testing, since it's a lot easier to test different scenarios (e.g. disk failures, replacements, adds) with virtual disks.

---

### Post by darkod on 2016-09-09
Did you try not raiding the EFI partitions? Also, make the EFI partition be the first one on the disk. And don't create the small 1MiB partition, that's for legacy boot only AFAIK.

The 1MIB area you say it added in front is probably unpartitioned space. It shouldn't create any partitions unless you tell it to but it is standard to leave the first 1MiB unused and the first partition to start from 1MiB on the disk.

Considering the EFI is for grub/boot, is it possible it should not be raided? Create identical FAT32 partitions on both disks and activate the boot flag on them, and try the installation like that.

Or, simply take my earlier advice and use legacy boot. Much more stable, less issues... :)

---

### Post by linwood2 on 2016-09-09
> **darkod said:**
> Did you try not raiding the EFI partitions? Also, make the EFI partition be the first one on the disk. And don't create the small 1MiB partition, that's for legacy boot only AFAIK.

The 1MIB area you say it added in front is probably unpartitioned space. It shouldn't create any partitions unless you tell it to but it is standard to leave the first 1MiB unused and the first partition to start from 1MiB on the disk.

Considering the EFI is for grub/boot, is it possible it should not be raided? Create identical FAT32 partitions on both disks and activate the boot flag on them, and try the installation like that.

Or, simply take my earlier advice and use legacy boot. Much more stable, less issues... :)

Yes, it works if I do not raid the EFI partition(s), and mark them EFI and bootable.  It definitely seems to be related to the raid.  I've done them in various orders.

On my "real" system, I just did an grub-install onto the second disks so both would have it, and tried booting with one unplugged, and it works.  So I'm good, it all works, I just don't fully understand if it should have worked as raid.

I have no idea if there's an advantage to me to having done UEFI, but I have working now, and might as well sip from the firehose of future progress a bit at a time.

---

