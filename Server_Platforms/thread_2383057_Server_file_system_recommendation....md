---
title: "Server file system recommendation..."
date: 2018-01-20
forum: Server Platforms
---

### Post by Chester_D._Kat on 2018-01-20
I have had an Intel Atom duel core 1.8 GHz, 4 GBs RAM server running at home for a number of years. Currently its running Debian 7 but I want to refresh with the latest LTS Ubuntu server release. I’ll use a 500 GB Samsung SSD for the boot drive. I have been running PLEX (no transcoding due to lightweight CPU), ownCloud (will use NextCloud with new install) tt-rss so Apache2, MariaDB etc. This box has been a file server and has 5- 2TB HD’s in a RAID 5.

I have been using ZFS for the RAID array but reading about its hunger for RAM am now hesitant to stick with ZFS. I have had the odd photo file or PDF that has been corrupted and speculate that perhaps this hardware is not up to running ZFS.

I’d appreciate knowing the consensus on what file system may be best for the above configuration, btrfs, ZFS or ext4.

Thank you for your time...

---

### Post by TheFu on 2018-01-20
ZFS is the only file system that deals with data corruption by validating what was sent to the disk is actually written.  ZFS is hungry for RAM when the advanced features are enabled like deduplication. Most standard things you would use ZFS for don't require much RAM at all.

OTOH, ZFS really shines when RAIDz2 is used.  Using RAID5 on disks over 1TB in size hasn't been recommended by storage vendors in a very long time. There are many reasons they don't recommend it, but mainly it is due to array rebuild time when a disk fails. On a home server that really isn't very busy, I doubt that matters.  I've seen RAID5 corporate servers take over a month to rebuild an array because the disk transactions never slowed down much.  I stopped using RAID5 when switching to 2TB and larger disks.

I wouldn't touch btrfs. There seems to be edge cases that still cause poor performance or data loss.  Most people don't have any issues with it, but Redhat has deprecated it.  SuSE is all in on BTRFS and makes it their default file system.

Ext4 is a good, general purpose, file system with good general performance and nice features when paired with LVM. 

Regardless of the choice, good backups are necessary.  The moderators expect me to write that, always. ;)

Without knowing the exact CPU and exact motherboard, it isn't possible to recommend a file system. Not sure I'd bother with an SSD for any server like this either. It just isn't necessary.  Nextcloud and Plex aren't high transaction or huge data pushing services, especially in a home.

My plex server uses a G3258 Pentium and has lots of storage without any RAID. I consider backups much more important, especially for stuff like media.  I use LVM + ext4. 
My nextcloud system runs in a virtual machine on a different physical host. It is only accessible from the LAN or through a VPN connection. It is very light compared to most other services running.  I keep most of the data that nextcloud can see on other systems and make it available through read-only NFS mounts to the nextcloud system. No risk of accidental file deletion that way.

---

### Post by Chester_D._Kat on 2018-01-21
Thank you for all your input. You have helped me a lot! The motherboard is: [h=1][FONT=inherit]SUPERMICRO MBD-X7SPE-H-D525-O Flex ATX Server Motherboard FCBGA559 DDR3 800[/FONT][/h]It dates back to 2010 when I bought it new. It is still up to the tasks that I am looking to accomplish (I believe).

---

### Post by TheFu on 2018-01-21
Looks like it has a D525 CPU.  That CPU doesn't have AES extensions and because the Atom is slow, you'll want to avoid any encryption - encrypted storage or encrypted VPN connections or Nextcloud encrypted storage.

BTW, the latest Ubuntu LTS is 16.04.  I won't be touching 18.04 until July, at the earliest.  My data is worth being cautious.  New is the enemy of stable, after all.

---

