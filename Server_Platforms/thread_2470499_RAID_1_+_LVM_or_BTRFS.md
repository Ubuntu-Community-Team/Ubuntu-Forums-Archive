---
title: "RAID 1 + LVM or BTRFS"
date: 2022-01-01
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2022-01-01
I'm looking to dump snapraid & mergerfs. I just now was trying to remove a disk from the pool and rsync the data off of it, smart data looked bad. It was a nightmare. Kept removing disk and mounting elsewhere then getting transport endpoint not connected. This may be due to a few binds I had into the pool.

At any rate I'm debating lvm on top of raid 1, else btrfs. I'd prefer to use btrfs but my goal involves everything being on a single mountpoint or nfs shared location. LVM and raid 1 I get, simple. BTRFS I'm not understanding how I could add another raid 1 in the future and extend the volume? to the additional raid 1?

Of course this is all media and should I worry too much about this stuff is the other question i.e. just go with what I know with raid 1 and lvm?

---

### Post by TheFu on 2022-01-01
btrfs isn't completely safe if more than 1 drive is part of the pool.  Read the Ars Technical article about it, carefully. For a laptop with a single disk, btrfs is interesting. For any system with multiple storage devices and plans to put them into the same pool, not so much. My data is important. I'd rather not risk it.

If you use any virtual machines, probably best to avoid using btrfs too. You can look up the reasons.

LVM has RAID1 capabilities built in, no need for mdadm, unless you just prefer having more complexity.

Why no ZFS in consideration?  RAIDz and RAIDz2 are perfect for media.

Ok - full disclosure.  I have a media server that also runs a few VMs.  I'm using LVM, no RAID.  The LVM storage for the OS and personal (non-media) files are backed up nightly, with automatic, versioned, backups.  I don't recall the number of versions, but at least 90 days. Perhaps 120. IDK.  Each VM is treated just like a regular physical machine. Backups run inside the VM.

The media storage uses LVM, no RAID. To backup those files, I use **rsync** periodically, about 3x a week.  I just don't have enough storage to use versioned backups. None of the LVM storage VGs or LVMs cross physical drives. I learned a hard less about that years ago.  Also, I've standardized media LVs on 4TB sizes, which turns into about 3.6TB after formatting. LVs are allocated smaller than needed and grow over time, as needed.  Just this morning, I added 40G more to a full LV.  The VG holding the LV still has 29G free.
```
  VG             #PV #LV #SN Attr   VSize    VFree  
  istar-vg         1   3   0 wz--n-   <3.64t      0 
  istar-vg2        1   1   0 wz--n-   <3.64t  29.04g
  istar-vg2-back   1   1   0 wz--n-   <3.64t   5.04g
  istar-vg3-back   1   1   0 wz--n-   <3.64t  <8.39g
  istar-stuff      1   1   0 wz--n- <298.09g      0 
  istar-8TB        1   2   0 wz--n-   <7.28t  14.03g
  istar-8TB-B      1   4   0 wz--n-   <7.28t <37.79g

```
Don't worry about the names. I should be more consistent.  The "back" in the names originally meant it was for backups, but those are all moved to the 8TB disks now. star-stuff is temporary space ... on a 320G Seagate that just keeps going and going the last 13 yrs or so.  None of my 320G Seagate disks have failed - they were bought around 2006-2007 for a RAID array back when Seagate engineering was excellent.

Also, on the media storage, I've set all file system reserved blocks to zero. The typical 5% reserved blocks was way too much storage to waste.  Of course, for the OS LV, 5% is a reasonable amount to reserve.

Every time I add new storage to the media server, I consider using ZFS, but I'm usually in a hurry or just had a disk failure. I need more practice with ZFS.  I should put it on a play disk for some use.  
While a disk failure isn't the end of the world, there is a recent copy available, running without any backups for about a week for the failed storage bothers me.  The HDD that failed the most in my media server was the drive that holds the OS, swap, and media DBMS. Basically, the drive getting the most, hardest, use.  Last time I replaced it with a "WD Gold" HDD, which is a datacenter duty cycle HDD. So far, so good. The 2 prior disks were 4TB "desktop" HDDs - one from Hitachi and the other from WD. Both failed just after the warranty period ended.

Hope this is helpful.

---

### Post by ameinild on 2022-01-05
+1 for ZFS - much more mature than BTRFS, easy to use and rock solid.

---

### Post by Tadaen_Sylvermane on 2022-01-05
Ill give zfs a look first then. Appreciate the viewpoints.

---

### Post by TheFu on 2022-01-05
On Ubuntu, ZFS is ready for use for data only, not the boot or the OS files.

The Ars article about BTRFS: [https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/](https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/)

---

### Post by MAFoElffen on 2022-01-06
> **TheFu said:**
> On Ubuntu, ZFS is ready for use for data only, not the boot or the OS files.
LOL. Well-- Yes and No. It all depends on the installation media.

You can install ZFS-on-root (booting from ZFS) from the Ubuntu Desktop install media, but is not offered on the Server Install media. Everything will be ZFS except the EFI partition...

What I do to install an Ubuntu Server on a ZFS root is to do a minimal install of zfs-on-root from the desktop install media. Then convert the network management from network-manager to netplan...Then convert it to server using
```

sudo apt install ubuntu-server

```
Once slimmed down and coverted to server edition, then install my server services.

---

