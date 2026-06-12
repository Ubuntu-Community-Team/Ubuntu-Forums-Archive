---
title: "zfs detach failing due to accidental add"
date: 2011-01-11
forum: Server Platforms
---

### Post by Rhadamanthos on 2011-01-11
Hi all,

I realize this isn't a ZFS help forum, but I figured someone might know something. I'm playing around with ZFS on Ubuntu (64-bit 10.10 using zfs-fuse).

I've just done a very dumb thing. I have several drives I'm messing around with ZFS on (fortunately, all my data is backed up on other disks!) and I did an incorrect add.

My original pool was made in this way:
zpool create pool1 raidz sda sdb

So now I have two disks in a RAID-Z array. I did my add like this though:
zpool add pool1 sdc

This led to a non-RAIDZ, non-mirrored drive being placed in the pool, like this:

	[INDENT]NAME        STATE     READ WRITE CKSUM[/INDENT]
	[INDENT]pool1       ONLINE       0     0     0[/INDENT]
	  [INDENT][INDENT]raidz1-0  ONLINE       0     0     0[/INDENT][/INDENT]
	    [INDENT][INDENT][INDENT]sda     ONLINE       0     0     0[/INDENT][/INDENT][/INDENT]
	    [INDENT][INDENT][INDENT]sdb     ONLINE       0     0     0[/INDENT][/INDENT][/INDENT]
	  [INDENT][INDENT]sdc       ONLINE       0     0     0[/INDENT][/INDENT]

Now it won't let me detach sdc ("only applicable to mirror and replacing vdevs") because there might not be other copies of the data. There's enough space on the array to shrink it down to just sda and sdb, because I didn't add anything after adding sdc, but I don't know if there's a way to shrink the array or pull sdc out of the pool.

Anyone have any ideas? If not, I'm going to grind the array to dust and re-instantiate it, but if I didn't have all the data on other disks, I'd be pretty hosed at this point...

---

