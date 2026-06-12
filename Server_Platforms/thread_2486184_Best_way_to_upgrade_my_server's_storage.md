---
title: "Best way to upgrade my server's storage?"
date: 2023-04-22
forum: Server Platforms
---

### Post by shawnsg on 2023-04-22
Hi,

Hopefully this is a good place to ask.

I've got an Ubuntu Server that I run at home that does a whole host of things, from Nextcloud to Plex to HomeAssistant to Minecraft. The way I have my drives configured is a little sub-optimal; I have a 2TB HDD I started with, and a second 4TB I threw in when the 2TB got to be full. Since I just haphazardly installed the second drive, I now have a situation where any files I want to store in mass are spanned across `/mnt/1` and `/mnt/2`.

I'm starting to run into a situation where 6TB is not enough (this would have completely bewildered me if you told me that a year or two ago). As such, I'd like to get new drives, but I really don't want to have to deal with a `/mnt/3`. What I'm wondering, then, are my options for spanned storage, and what anyone might recommend from experience. I was initially considering just a standard RAID configuration, but I've seen things about LVM, TrueNAS, ZFS, and whatnot that make me wonder what the best approach would be.

For my use-case, my main concerns are parity and expandability. Larger capacity drives can get expensive, and I don't want to have to either buy a chunk of drives, and be stuck with that capacity until i buy a newer, bigger chunk, or just shell out more than I can reasonably afford to have to avoid that. I'd also like to have some sense or parity, so that if one of the drives kicks the bucket, it doesn't take everything offline.

As is, I think what I would want to go for is playing with LVM. But I'm not 100% certain, and I don't really want to risk data loss. So please let me know what you might recommend for this use-case, if you've got a little more experience than I do :P

Thanks!

---

### Post by TheFu on 2023-04-22
Step 1.  Backup all the data.  Setup daily, automatic, versioned backups.  The size of your backup storage "chunks" will determine how large you should/can let any complex volume management be.  I use 4TB as my "chunk size" - no file system is allowed to be larger than what a 4TB HDD can support ... which turns out to be about 3.6TB.

I've used mdadm (Linux software RAID) and LVM for over 20 yrs now.  Both require backup storage, so if I need 6TB usable, then I'll have 6TB just for backups and sync daily using rsync.  This is for media. 

For non-media files, I use a normal backup tool to backup everything needed to recreate the machines within 30-45 minutes. Since I have 10-15 machines at any time, it would be a terrible day if all of them needed restoring at once.  I've had 2 virtual machines need to be recreated after I did something dumb.  At the same time, I decided to upgrade the OS (which was needed anyway). It took a little longer than 45 minutes, but saved doing the OS upgrade later.

About 20 yrs ago, I was using LVM to span file systems across multiple disks.  I didn't have backup religion at the time, but didn't have any problems spanning across an 80G, 120G and 80G HDD set.  Then the unimaginable happened. One of those drives failed.  All data on all 3 disks was lost.  I probably have those disks on a shelf somewhere and could probably restore some of the files today (I have more knowledge now), but it is 20+ yr old data, so why bother?

Around 2008, I got backup religion.  This was after about a decade of professionally designing systems for redundancy against all sorts of failures, including an entire data center outage (which I've not seen).  Our data centers had 20K servers in them and they were all class 5 with multiple power substations, multiple internet connections, and built inside hardened buildings that would survive any weather events.  Anyway, even with all that knowledge and a huge personal data loss, I didn't get backup religion, until my little company had employees and I know that if we lost the client data, we'd all be out of work.  Not a big deal for me, but one of the employees was a single mother and needed the paycheck.

Depending on the types of files, you may not need to do anything special. For example, every media server software easily merges media files from different disks into a single view.
```
Type  Size  Used Avail Use% Mounted on
ext4   54G   15G   38G  28% /var
ext4   26G  9.9G   15G  41% /home
ext4   20G  7.1G   12G  39% /var/lib/jellyfin
ext4  294G   66G  228G  23% /TV
ext4  3.5T  3.5T   34G 100% /d/D1
ext4  3.6T  3.6T   23G 100% /d/D2
ext4  3.6T  3.6T   74G  98% /d/D3
ext4  3.6T  211G  3.2T   7% /d/D6
ext4  3.6T  599G  2.9T  18% /d/D7
ext4  3.6T  3.5T  140G  97% /d/b-D1
ext4  3.6T  3.6T   27G 100% /d/b-D2
ext4  3.6T  3.6T   79G  98% /d/b-D3
ext4  3.6T  211G  3.2T   7% /d/b-D6
ext4  3.4T  600G  2.7T  19% /d/b-D7
```
Can you guess which contain backups?  Those are each LVM Logical volumes.
Under D[1-7]/ there are M, T, V, Photos, and a few other directories. These get merged into a single view by Jellyfin (formerly plex and formerly Kodi).

I'm more concerned that you have multiple complex, heavy, programs running directly on a single OS install.  I'd strongly recommend that you look into virtual machines and linux containers to keep complex software stacks separate.  For example, the disks above are mainly for NFS, Jellyfin and mpd use.  The system runs a few Linux Containers - one has a Wallabag server, another has a Nextcloud v24 server.  In this way, the main OS software dependencies are completely removed from both Wallabag and Nextcloud.  On a different system, I have a VPN virtual machine to allow remote access into my LANs.

To show the LVM stuff, 
```
$ sudo pvs
  PV             VG             Fmt  Attr PSize    PFree   
  /dev/nvme0n1p3 vg00           lvm2 a--  <464.98g <189.88g
  /dev/sda3      istar-vg       lvm2 a--    <3.64t       0 
  /dev/sdb3      istar-vg2-back lvm2 a--    <3.64t   44.00m
  /dev/sdc1      istar-vg3-back lvm2 a--    <3.64t   <8.39g
  /dev/sdd1      istar-stuff    lvm2 a--  <298.09g       0 
  /dev/sde3      istar-vg2      lvm2 a--    <3.64t   19.04g
  /dev/sdf1      istar-8TB      lvm2 a--    <7.28t    8.03g
  /dev/sdg1      istar-8TB-B    lvm2 a--    <7.28t  <37.79g
  /dev/sdh1      WDBLK_8T       lvm2 a--    <7.28t  <59.23g

$ sudo vgs
  VG             #PV #LV #SN Attr   VSize    VFree   
  WDBLK_8T         1   3   0 wz--n-   <7.28t  <59.23g
  istar-8TB        1   2   0 wz--n-   <7.28t    8.03g
  istar-8TB-B      1   4   0 wz--n-   <7.28t  <37.79g
  istar-stuff      1   1   0 wz--n- <298.09g       0 
  istar-vg         1   3   0 wz--n-   <3.64t       0 
  istar-vg2        1   1   0 wz--n-   <3.64t   19.04g
  istar-vg2-back   1   1   0 wz--n-   <3.64t   44.00m
  istar-vg3-back   1   1   0 wz--n-   <3.64t   <8.39g
  vg00             1  11   0 wz--n- <464.98g <189.88g
```

Note that no VG has more than 1 PV.  I don't span VGs across disks anymore. Losing all that data years ago taught me that lesson.

I'm not comfortable showing the **lvs** output. It would be confusing to many people, since I use LVs for virtual machines, Containers, and other special storage needs.  For simple uses, an LV (logical volume) can be considered a really smart partition.

Nobody has a perfect storage setup.  I certainly don't.  But the system above has had a few HDD failures over the years and survived.  2 of those failures were with the 4TB OS drive. About 18 months ago, I swapped that out for an NVMe SSD.

If I run out of storage again, I'll either add D4 and D5 back in as 4TB disks (or 4TB LVs from 8TB or 12TB or 16TB drives split into 4TB chunks). I go out of my way to have no primary storage connected via USB.  USB connected storage is only used for backups. No exceptions. The USB storage command set isn't the same as SATA, eSATA or SAS connections.

One of the best things I've ever done was to get a cheap plastic internal drive cage with a caddy system that supports hot-swapping disks. It converts a (3) 5.25inch front panel into a (4) 3.5inch set of bays. These each are connected to internal SATA ports.  Easy access. Fast.  Had the cheap fan die a few years ago. Swapped in a Noctua fan. I wish the bay system was $20, but even at $50, it has made dealing with HDDs easier. No need to remove the case panels.  Just a flip of a spring-loaded caddy and a drive is available. Wish I'd bought another at the same time of my other mirrored system.  

I have 2 external 4-drive disk arrays too. I'd rather have those drives in the internal drive cage. Both systems have so much storage connected that I needed to add another JBOD SATA card to support them all.

If I were you, I'd buy (2) 8TB Black HDDs with 5 yr warranties when they are a deal.  Life is too short to deal with data loss over stupid drive choices.  If a HDD doesn't have a 5 yr warranty, I'm not interested. Been burned too many times with 1 and 3 yr drive warranties.  The warranty really says how much the manufacturer believes in their disks.  5 yr warranty drives means they think they will last "forever" ... which is over 10 yrs.  I've had a number of blue, green, and even red HDDs fail over the decades.  When I say WD-Black drives, that's a specific line of internal spinning disks.  Sadly, sometimes the vendor will try to abuse the "black" marketing term for inferior cheap USB external drives just because the external case happens to be black in color.

TrueNAS, ZFS are the same thing.  TrueNAS uses ZFS.  Nothing wrong with ZFS, but there are some important storage considerations with ZFS that aren't so clear.  If you have backups, most of those issues that come with RAIDz, RAIDz2 and RAIDz3 become unimportant, since you don't need those RAID levels, especially in a home environment.  For most home users, RAID (any level) is a good way to have data loss immediately propagated across all your storage.  But if you have versioned backups, that risk and 101 others are mitigated.

---

