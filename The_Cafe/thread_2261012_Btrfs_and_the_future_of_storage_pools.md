---
title: "Btrfs and the future of storage pools"
date: 2015-01-15
forum: The Cafe
---

### Post by kayot2 on 2015-01-15
Hello, I'm a long time reader of this forum. I need to talk about btrfs since my friends have no idea what I'm talking about and why I'm so excited.

So I've recently built a real server for my files and streaming etc. 

Specs, not related, but in case anyone wants to know:
[COLOR=#00B300][FONT=Georgia]IBM ServeRaid M1015 PCI-E 8-port SAS-SATA Controller Card SAS9220-8i 46C8933 -> Cross Flashed to [/FONT][/COLOR]**LSI9211-IT**[COLOR=#00B300][FONT=Georgia]
[/FONT][/COLOR][COLOR=#141414][FONT=Georgia]2 of [/FONT][/COLOR][COLOR=#B30000][FONT=Georgia]Crucial 8GB Single DDR3 1600 MT/s (PC3-12800) CL11 Unbuffered ECC UDIMM 240-Pin Server Memory CT102472BA160B
[/FONT][/COLOR][COLOR=#0059B3][FONT=Georgia]Intel Xeon E3-1220V3 Haswell 3.1GHz LGA 1150 80W Server Processor BX80646E31220V3[/FONT][/COLOR]
SUPERMICRO MBD-X10SLM-F-O uATX Server Motherboard LGA 1150 Intel C224 DDR3 1600

So I was reading about different file systems and what not since I have 9 2TB preexisting 80% full drives from a windows server system formatted in NTFS. I wanted to convert them to native linux file systems. I custom compiled the kernel to allow aufs and enable hnotify to avoid whiteout files from being a problem. It works great by the way, instruction are here -> [http://blog.asiantuntijakaveri.fi/2014/07/adding-aufs-support-to-3.html](http://blog.asiantuntijakaveri.fi/2014/07/adding-aufs-support-to-3.html)

So I was going to go with EXT4 since it's well supported and has been tested extensively. My eventual plan was that once I purchased 10 3TB Green Drives (maybe 4TB if the price goes down a notch) and WDIDLE3 them to no timeouts, that I would put together a FreeNAS ZFS machine and call it. My goal was to keep the drives available until that day. Besides, the instructions for compiling the kernel were very specific so I was going to be stuck on 14.04.1 LTS. That means I wouldn't have access to newer implementations etc. My final plan was to use the 2TB drives + whatever I needed, to keep a backup and the data would be on the ZFS with a RAIDz2. I had to have all the drives before I could start since a ZFS is locked at the number of drives with raid functions.

I accepted this. Aufs isn't going to be in the kernel and recompiling it (with hnotify) was a lengthy procedure. Mhddfs is Fused base which has its own pitfalls. NTFS is old and lacking of newer features, such as checksums, and in ZFS's case, healing abilities when in a raid.

So I'm reading, and reading, etc. I remembered hearing about btrfs back in 2012 and decided to check it out.

It was like night and day. Dynamic volumes, adding and removing them without data loss, and now with experimental raid 5 and 6. This is huge and no ones talking about it. 

I can take a drive, convert it to btrfs, put data on it, add another drive, rebalance, add more data, add another drive, rebalance, add more data, if enough space is free I can turn it into a raid 5, add another drive, turn it into a raid 6, add anther drive, rebalance, loose a drive (don't replace it), repair, rebalance. 

All of that and it will still work. In November 2014 they added scrub/replace commands. It's a wet dream come to life.

For those who don't know, half of what I just listed is impossible for anything else. Adding raid 5 and 6 to that is just crazy. In my case, instead of waiting until I have all 10 disks, I can use 4 to start with a raid 6, then add disks as they arrive. I don't know if the drives stay online for this though. That would really be too much. I'm guessing rebuild times are going to be outrageous. Then the chance that I can lose the array during every step. With a full backup, it might be worth trying.

I'm not sure how plausible all the above is, however most of the raid work has been done recently. So, if you want to correct any of the above, keep in mind that this is a recent development. I'm currently experimenting with VMWare to see how these concepts hold in real life. I'm defiantly excited. The system also supports asynchronous deduplication. That's a really nice feature to have with no real downsides to deployment. To finish up, btrfs supports early abort compression which means it wont compress something if it can't compress the first 4096 bytes, so it skips it and moves on saving time in the process. A flag on compression can force it to do compression always, but isn't all that advisable.

All in all, a nice file systems worth noting.

---

### Post by grahammechanical on 2015-01-15
I experimented a little bit with btrfs on a desktop install. I came to the conclusion that it is definitely a file system for servers more than desktops. It lacks a GUI snapshot manager to make it acceptable for the desktop user.

If we install apt-snapshot then whenever we update a snapshot of the system will be created automatically and the Recovery mode menu will give us an option called apt-snapshot - revert to old snapshot and reboot.

I run the development release. So, I do not see much benefit to using brtfs as I update daily and am always ready to re-install. A couple of us experimented with using brtfs snapshot to rollback from a Ubuntu version upgrade to the old version. It works as well. 

It is worth while for a server system administrator to learn how to administer a btrfs file system but for a desktop user it would require a little too much learning. It does need a GUI btrfs management utility before it can become the default file system for Ubuntu desktop installs.

There is one other downside. If we install Ubuntu onto a btrfs file system then Grub will put that installation into the Grub boot menu but Grub cannot detect any existing installs of Ubuntu that are on btrfs partitions. I have several installs of Ubuntu for testing. With them all on btrfs it was a lot of effort modifying the Grub configuration files so as to get those installs showing up in the boot menu.

Regards.

---

### Post by kayot2 on 2015-01-15
I agree that it's defiantly targeting servers. I'm using an EXT4 system for the / on my server. I'm told that I should use something else, but I don't mind. The OS is just a means. The real valuables are the storage drives. Since my server is for files and streaming (until I build a HTPC from the old server components which where Desktop grade) I'm not concerned about grub. My current setup is 9 2TB drives with 2 working as Parity. I'm using Aufs with hnotify, and SnapRaid.

I wish I knew how to program ssh programs like midnight commander. I'd love to make a suite of programs that work over ssh. I think it would be fun to make one for btrfs, samba, nfs, and configuration. I'd also make one that simplified aufs construction.

I have a question regarding snapshots. Lets say I make weekly snapshots. Then I delete a file, but before that, I've been doing some cleaning and I deleted a bunch of other files too. I want that one file back, but I don't want the others. How possible is it to just grab that one file from the snapshot and leave the others to their digital fate?

---

### Post by ventrical on 2015-01-16
I hadn't tried that during my work with btrfs. I am not sure it is possible but there may be some index command structure that might allow it.  When I first used it I thought it was a novelty but as graham has pointed out , it kept failing in GRuB and there was a lot of downtime. It is faster to just re-install these days.

Regards..

---

### Post by The Cog on 2015-01-16
> **kayot2 said:**
> I have a question regarding snapshots. Lets say I make weekly snapshots. Then I delete a file, but before that, I've been doing some cleaning and I deleted a bunch of other files too. I want that one file back, but I don't want the others. How possible is it to just grab that one file from the snapshot and leave the others to their digital fate?

Bear in mind that a snapshot is visible and looks like a subdirectory in the root volume. So you can always just navigate to the file in the snapshot and copy it to the "live" subvolume. Doing so will result in a new copy of the file on disk though - it's not just replacing the severed linkage from the "live" subvolume to the same are of the disk that contains the snapshot copy. I don't know if btrfs has its own copy utility that copies just by making new btree linkages to the existing file contents - I haven't read about any such utility.

P.S. 
The Ubuntu installer creates the two subfolders @ and @home for the root and the /home filesystems if you install on btrfs. If you want to install another OS version on the same btrfs, I have only ever done it by (for instance) renaming @ to @ubu-12.04 before re-running the installer. But as has been noted, grub / grub-install don't find the other system subfolders, so 12.04 doesn't get offered as a boot option any more. For this reason, I find it better to maintain separate non-btrfs partitions for / or /boot.

---

### Post by kayot2 on 2015-01-16
So I've been playing with btrfs and I have to say... It's as awesome as previously thought. I've been trying to kill the array short of anything obvious. I've mixed them up, removed two and shrunk the array instead of replacing the missing drives. Something I've noticed is that I went overboard when I set the metadata to raid 6. A mirror on that is probably fine.

I went ahead and used snapshots and subvolumes. I understand how that works now. Some of the commands aren't intuitive but at least they all use 'btrfs' as their start. I haven't used scrub since this is a VMware test system and that would prove pointless. Something that annoys me right now is how the device reports free space. If I put four 30GB drives together under a raid 6, it reports it as 120GB of free space. However; due to the parity, that is misleading. I understand why it does it, since I can use mismatched drive sizes and still have all the file space available.

I haven't played with deduplication, but compression works fine. I prefer lzo since it's faster and I don't expect much from it.

I'll defiantly try using this when I get enough drives to make a proper backup. I think I'll use EXT4 on the backups since that seems like the default in ubuntu.

Side question: Do any of you know of software that would work on a headless machine, that will allow me to make a backup of all the data on a btrfs array onto single drives?

I ask, because even using ACHI I have yet to feel comfortable doing hot swaps. Since my case only has twelve hot swap bays and I'll be using 10 for data drives, I can only put two backup drives in at a time. This means I'll have to load up two at a time. What I'm looking for is something that will keep track of changes, only swap in drives if necessary, and will use hardlinks on identical files. I can probably make something in .net that would do that, but if it already exists, I don't want to reinvent the wheel.

---

### Post by ssam on 2015-01-17
Be careful with BTRFS raid5/6. The recovery code is only just landing in the kernel currently, it could easily take a few more kernel releases to shake the major bugs out and maybe a couple of years to get the rarer bugs. However the BTRFS raid1 code has been around for a few years now, and is working well for many people. Read through the BTRFS wiki before using it.

---

### Post by kayot2 on 2015-01-17
The documentation on the btrfs wiki is hit and miss. I understand why. This thing is a moving target from hell. I'd do a write-up but I don't have anywhere to post it. Maybe I should do it on the Wikipedia?

---

