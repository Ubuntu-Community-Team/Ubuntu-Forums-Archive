---
title: "Need help planning a home storage server - md, lvm, zfs?"
date: 2018-04-29
forum: Server Platforms
---

### Post by xianath2 on 2018-04-29
I'm (re)-building my home NAS. It's currently built using md RAID6 (12x1TB) with LVM2 on top and a mix of ext4 (/ and /boot) and xfs (everything else.) It's been serving me well on an off since 2008, but it's time to retire it. I have 6 brand new 6TB disks for that purpose which would more than double my current capacity, so I won't even need to do funky things like online-expanding the current array. Just build a new one, copy over the data, and then expand it as needed.

Since ZFS is now available on Linux, should I look into that more seriously? One of the major limiting factors for me is that it can't (yet) do online array expansion. Would it make sense to build the array using md, then either LVM2 on top and use LVs for ZFS, or simply build the zpool directly on top of md? If I grow the md array organically as I purchase more drives, can ZFS handle the resizing of underlying devices? Should I expect any significant performance issues or incompatibilities between zfs and md (and lvm?) Will I need to take care of things like ashift and block size or is the stack smart enough to detect those? Also, how much RAM should the box have for a 36T (and more) zpool, assuming no deduplication or compression is used? Questions, questions...

---

### Post by LHammonds on 2018-04-30
I had the option with Veeam Backup and Recovery to utilize Linux as the backup repository but as you have noticed, the tools just don't allow for dynamic expanding of storage.  I evaluated this about 4 years ago. You have to shutdown the server to make changes.

I forgot how many terabytes the system reached before it was incapable of dynamic resizing but it wasn't much for a NAS.  The dynamic resizing works great for normal servers but not huge data repositories.

I was forced to go with Windows 2012 for the main reason of not being to dynamically allocate on-the-fly.  But if you plan to allocate all your storage during initial creation, it might no be a bad way to go.  But if you ever add more later, you will need to know the steps on how to expand the system while offline and I'd recommend documenting how to do this safely at the beginning BEFORE you start putting valuable data on it.  Test and document everything you need to do before needing.  That is why I have documented my server installs like I have done (such as showing how to add additional drives, include into the LVM and how to increase the partition and file systems.

LHammonds

---

### Post by xianath2 on 2018-04-30
Not sure where my reply went, I posted from my phone but I don't see it here... anyway.

I'm pretty comfortable around md and lv, and I've done pretty much anything that makes sense with that combo. I have zero experience with zfs though and I want to make sure that I won't hit a roadblock further down the line that I won't be able to recover from. Hence my questions:
[LIST]
[*]If I build a zpool out of a single md device as a vdev, can zfs handle online expansion of the underlying device?
[*]Likewise, but with an LV as a vdev
[*][LEFT][COLOR=#222222][FONT=Verdana]Should I expect any performance degradation from using zfs on top of md RAID6? Specifically, will zfs adjust its own (dynamic) block size to the underlying strip and stripe sizes?[/FONT][/COLOR][/LEFT]
[*][LEFT][COLOR=#222222][FONT=Verdana][/FONT][/COLOR][/LEFT]Is the zfsonlinux stack smart enough to detect things like block size, minimum and recommended iosize in the above configurations?
[*]If not, can these be forced?
[*]I'm still trying to understand how far along md journal work has come. Is it as good as the zfs intent vdev? Can I use three SSDs in a RAID1 configuration to speed up writes to my RAID6?
[*]If not, and [LEFT][COLOR=#222222][FONT=Verdana]I build the zpool in this way as a single vdev built on top of a RAID6 md device, will I be able to add an intent and/or cache device to the zpool, assuming I have three SSDs to spare? If yes, will I be able to force them to a three-way-mirror configuration given that the vdev itself is not redundant?[/FONT][/COLOR][/LEFT]
[/LIST]
[LEFT][COLOR=#222222][FONT=Verdana]&#8203;
I know that's a lot of questions but I hope you understand I can't just throw money at this thing and I'm trying to be smart about it. Last time I built a NAS, I did so much research, I actually turned it into my master's thesis (no kidding!) I'm a bit old for that now but old habits die hard. Thanks for any help.
[/FONT][/COLOR][/LEFT]

---

### Post by LHammonds on 2018-04-30
Well, I'm not one that can answer those specific questions which are related bare-metal installs.  All my installs have only been as virtual machines utilizing IBM storage so it handles all the RAID.  I only have to worry about the OS capability at the VM level.

But I hope you are not building a single monolithic storage system that has no equal and cannot be backed up.  I would want 2 systems that mirrored each other and if one wasn't working out as expected, "could" dump and re-configure the backup unit (such as changing RAID or file system) to see if the new configuration could take over and become the primary and then rebuild the other to match.

Good luck with it and no matter what advice you get, be sure to do some small-scale testing before making a large commitment.

LHammonds

---

### Post by xianath2 on 2018-05-02
I'm afraid I don't have the luxury of setting up an enterprise solution, it's just a home server for my photography and video work, so I can't afford to replicate the whole system or even parts of it. I need to get it right the first time. Appreciate the support, now I guess I'll just wait and see if anyone's done anything similar before. If all else fails, I'll just set it up without ZFS at all.

---

### Post by LHammonds on 2018-05-02
Something I plan for a home network is the use of Raspberry Pi's due to the low power usage and need to be online all the time.  One will be a domain controller, another will be the network storage.  The storage will scripted to replicate to another machine when it comes online once in a while.  Nothing fancy but should work OK.  I won't be using any kind of raid.  My backup solution will be the secondary machine along with offsite/encrypted backups.  ZFS will be my file system of choice though.  But this project will be late summer.

LHammonds

---

### Post by supermorph on 2018-06-02
just a thought, could it be worth having a dedicated drive for the os, make it use ext4, and then use btrfs for the nas storage? 
would also suggest a backup of the os drive so u can have quick restore to working status (i may be preaching to the quire here lol sorry)

i have just looked up specs for the btrfs and found this on the wiki of kernel dev page



 Major Features Currently Implemented

    Extent based file storage
    2^64 byte == 16 EiB maximum file size (practical limit is 8 EiB due to Linux VFS)
    Space-efficient packing of small files
    Space-efficient indexed directories
    Dynamic inode allocation (question to anyone in the know: could this mean online expansion?)
    Writable snapshots, read-only snapshots
    Subvolumes (separate internal filesystem roots)
    Checksums on data and metadata (crc32c)
    Compression (zlib, LZO, ZSTD), heuristics
    Integrated multiple device support
    File Striping
    File Mirroring
    File Striping+Mirroring
    Single and Dual Parity implementations (experimental, not production-ready) 
    SSD (flash storage) awareness (TRIM/Discard for reporting free blocks for reuse) and optimizations 
    (e.g. avoiding unnecessary seek optimizations, sending writes in clusters, even if they are from unrelated files. This results in larger write operations and faster write throughput)
    Efficient incremental backup
    Background scrub process for finding and repairing errors of files with redundant copies
    Online filesystem defragmentation
    Offline filesystem check
    In-place conversion of existing ext2/3/4 and reiserfs file systems
    Seed devices. Create a (readonly) filesystem that acts as a template to seed other Btrfs filesystems. 
    The original filesystem and devices are included as a readonly starting point for the new filesystem. Using copy on write, all modifications are stored on different devices; the original is unchanged.
    
    Subvolume-aware quota support
    Send/receive of subvolume changes
    Efficient incremental filesystem mirroring 
    Batch, or out-of-band deduplication (happens after writes, not during) 


it also looks like thier planning to implement online fsck checking too in the future, so that could be really useful

hope this helps

---

### Post by TheFu on 2018-06-05
ZFS merges md, RAID, lvm and file systems into a single tool. Putting ZFS onto md doesn't make sense. If you were planning to run RAID6, then setup zfs with RAIDz2. You might want to consider an SSD added to the zpool as a caching device. 

To get a feel for how ZFS works, suggest building a VM with  6 small virtual HDDs.  Use those to try things out.  Add 2 more virtual HDDs and practice adding those 2 into the existing pool for a total of 8. And you'll want to decide on the backup method you want to use. Traditional or zsend to another ZFS setup?
RAID-whatever can never replace backups.  Just look through these forums for all the people with RAID issues where the only fix is to wipe and start over... using backups.   RAID solves 3 issues.  Backups solve 1001+ issues.

I wouldn't touch btrfs.  Just check these forums for all the issues that btrfs users are seeing.  The least of which is that btrfs lies about the actual storage used so du and df can't be trusted.  If you do virtualization, there have been bad performance issues running VMs on btrfs.

---

