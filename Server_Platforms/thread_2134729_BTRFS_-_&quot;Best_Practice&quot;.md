---
title: "BTRFS - &quot;Best Practice&quot;"
date: 2013-04-12
forum: Server Platforms
---

### Post by litch84 on 2013-04-12
What BTRFS doesn't have is a recent "Best Practice" list - there are a few from last year, but it's come leaps and bounds since then.
What I've found BTRFS does have is a whole bunch of pages going "HOWTO: Hey, you can have your laptop HDD as BTRFS". How Amusing. Appropriate if you're looking to do snapshots but otherwise pointless I would imagine...

I need some advice on what I should do; I already have a fair idea of what that is, but I want a 2nd, 3rd+ opinion.


[LIST]
[*]Ubuntu 12.04LTS x64 Server
[*]1 x 6TB and 2 x 9 TB RAID 5 logical disks off a RAID HBA
[*]Previously running ext4 until that went sideways on one of the arrays (by fault of my own).
[*]About 14TB of data as of now.
[/LIST]

I'd like to combine the arrays as one volume - and there are many means to do so (ZFS, LVM, BTRFS, etc...) - I'm looking for these features:
[LIST]
[*]Seamless integration, btrfs offers this with simply adding the disk to the filesystem and presto, LVM not so much, ZFS I have no idea.
[*]Recovery options, if one array goes kaput or if the UPS goes boom - how damaged is the file system, and how easy is it to recover? (BTRFS also exceeds here with the standard COW filesystem and ability to mirror metadata, but the FSCK tool may still need development).
[/LIST]

So the questions are:
[LIST=1]
[*]At what point in the btrfs development chain in the Ubuntu kernel (At the time of this post, my kernel is 3.2.0-39-generic).
[*]I would imagine mirrored metadata would be best practice for this purpose
[*]When I file is copied to this volume, is the file put on one device, or across both devices? In the case of the latter, then I may as well set the file to RAID-0 across both disks then (psudo-RAID 50).
[*]Depending on the answer to 2 and 3 - If one array was to suffer catastrophe - how recoverable would the data be on the remaining array? Would it still be mountable?
[/LIST]

Thanks in advance for your thoughts.

-KB

---

### Post by ssam on 2013-04-12
First read as much as you can on [https://btrfs.wiki.kernel.org/index.php/Main_Page](https://btrfs.wiki.kernel.org/index.php/Main_Page)

don't use a 3.2 kernel. a lot has changed in btrfs since then, and the developers are more concerned with getting new work into new kernels, than backporting fixes to old kernels. things are getting better, the 3.8.x stable releases have had several btrfs bug fixes (compared to a year ago where you might have been advised to run rc kernels to get fixes). you might find yourself needing to install newer kernels from the ubuntu mainline ppa.

probably best to give btrfs raw access to all the disks, rather than use a hardware raid underneath. Doing the RAID in the filesystem gives advantages, for example you only need to scrub or recover blocks that are actually in use. Also btrfs checksums all the data, so if there are 2 copies that dont match it knows which one is correct.

kernel 3.9 will have initial RAID5/6 support. I think it would be wise to wait a few kernel releases before using it. it is easy to re-stripe between raid-levels in btrfs. it just reads each block and writes it back out with the new raid level, the volume is usable while it is in a mix between levels. can you trim down your data to 12TB, or get hold of a few more disks? then you start with a btrfs raid1, and switch to raid6 in a years time to get some more space.

in terms of data safety, from reading the mailing list, it looks like btrfs will tell you very quickly (though not necessarily very politely) if you have any data corruption. other file systems may not notice. if this is important data, you ought to have another backup copy somewhere, raid only protects you against unreliable hardware.

---

