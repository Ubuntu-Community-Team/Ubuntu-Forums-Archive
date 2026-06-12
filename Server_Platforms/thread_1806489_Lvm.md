---
title: "Lvm"
date: 2011-07-17
forum: Server Platforms
---

### Post by Entilza on 2011-07-17
I'm setting up a new server and am using LVM.  LVM is totally new to me and seems very interesting at first I was a little unsure to use it but now it seems quite powerful.

I've setup the following Logical Volume groups:

/	20 GB
/var	20 GB
/home	20 GB
/tmp  	5  GB
/client 500 GB

This is my default setup, I've tested reducing/expanding partitions and I've managed to understand how to reduce the /client directory a little bit to increase /home for example.  I am just wondering if this is standard practice or should I do it the other way where I keep more % free in the physical volume and later just expand partitions as I need.

Do most of you split up these partitions in this format?  How often are you guys resizing LVM volumes, any issues? any comments?  Thanks

---

### Post by Entilza on 2011-07-18
bump, anyone doing many lvm resizes? :)

---

### Post by 1clue on 2011-07-18
I use minimal disk sizes and bump them up as necessary.

I only need to do it when I'm installing software or doing something relatively huge with data.  If you recycle your data space then after awhile you stop growing for that.

I try to keep my partitions more than 90% full for relatively static ones like /usr.  Actively written partitions where the data stays put I like to keep under 50% full, because I think the defragmentation algorithms work much faster and cleaner that way.

---

### Post by 1clue on 2011-07-18
> **Entilza said:**
> 
I've setup the following Logical Volume groups:

/	20 GB
/var	20 GB
/home	20 GB
/tmp  	5  GB
/client 500 GB


Oh yeah.  I don't do it like that.

First, I use tmpfs (which maps to swap) for /tmp and some other things.  I have a huge temp mapping (4xRAM, RAM is 12G) and then map various places where frequent high speed disk caching happens, but which need not stick around after reboot.  /var needs more room.

My setup is more like this, removing some of the more obscure mounts:
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/vg0-root  473M  365M   85M  82% /
tmpfs                  12G  608K   12G   1% /tmp
/dev/mapper/vg1-vm    373G   87G  286G  24% /vm
/dev/mapper/vg0-var   2.0G  987M  966M  51% /var
/dev/mapper/vg1-opt   938M   94M  796M  11% /opt
/dev/md0              510M   73M  411M  16% /boot
/dev/mapper/vg1-usr   4.7G  4.2G  315M  94% /usr
/dev/mapper/vg0-usr_src
                      473M  343M  107M  77% /usr/src
/dev/mapper/vg1-home  122G   79G   38G  68% /home

If you're wondering why some of those are so empty, I just did some system cleanup awhile back.  Also keep in mind that I removed some of the mounts because I think they're excess noise.

---

### Post by Entilza on 2011-07-18
Thanks for the suggestions I like the tmpfs suggestion I may use that for some future stuff.

So essentially I should reduce my /client directory for now to free up some PE units and save that for future expansion such as if home or var needs to grow I can expand it.

I guess you just tell your customer that there is still room to grow even though the partitions are smaller than they perhaps are expecting.

---

### Post by 1clue on 2011-07-18
Well for starters I'm my own customer on this system.

I have been building boxes for years, and was always frustrated by the inherent loss of space due to making partitions of the size I MIGHT need rather than the size I needed.

When I figured out lvm, all that went away.

FWIW the way I do it does take more maintenance.  When you upgrade sometimes you need to bump the LV size and start again.  Sometimes that's several times in one upgrade/install.  Sometimes you can keep System Monitor open (yes there are command line tools) and anticipate what is running out and stretch it before it actually runs out.  Ubuntu will warn you, if you're running with a full desktop.

I don't know if you noticed, but I have 2 volume groups spread across 4 drives.  Either volume group could contain the whole works, and then I have a non-LVM removable drive for external drag-over backups.

The idea is that if at some point one or more drives starts to go flaky I can add a drive to a VG, then retire the bad drive.

---

### Post by Entilza on 2011-07-18
So you have 4 drives 2 pairs of RAID 1?

Why not use RAID 5 and use all 4 drives?

---

### Post by 1clue on 2011-07-18
Actually the only RAID I have going is /boot, which is a 4-drive RAID1.

I don't want the performance hit of RAID5, and nothing on this system is so dear I can't live without it.

I've reformatted this system several times, been through the RAID thing and came back.  FWIW nothing I do here needs to stay up in the event of a drive failure, and there is no RAID configuration that protects against lightning strikes, so I'm making a backup anyway.  Why sacrifice speed?

So what I have is a total of 6 drives:
[LIST=1]
[*]Blue-ray burner, which works as a transportable backup for <= 50G
[*]A removable SATA drive which slot-loads, 1.5 TB, for backups.
[*]4x750Gx10K RPM identical drives to store data and OS.
[/LIST]

The 4x set has this on each drive:
[LIST=1]
[*]/boot, 4xRAID1, only RAID so they're always identical, but any drive can boot the system.
[*]SWAP partition of 12G.
[*]Linux LVM
[/LIST]

I am sacrificing a lot of safety net here, but I honestly don't care that much if the system goes down.  Nothing there is irreplaceable that isn't also on the backup disk.

---

