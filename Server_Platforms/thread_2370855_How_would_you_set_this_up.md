---
title: "How would you set this up?"
date: 2017-09-08
forum: Server Platforms
---

### Post by Richard_Thornton on 2017-09-08
Hi,

Your help will be much appreciated, thanks!

Hardware, all new so I can do anything on there:

Intel NUC7i5BNK
32GB RAM
2TB Samsung 960 (only disk so will probably boot OS from it)
Four 8TB drives connected by thunderbolt (I was thinking ZFS RAID 10 array)

Basically this is a home media server (minimum three file types movies, music, backups), it needs SMB at a minimum.

Basically I would like to use a large amount of the 2TB SSD as a funky cache, essentially I don't want file activities on the array to disrupt Audio (Roon, DSD is 2-3GB per album) / Visual (Plex, Bluray MKV is 20-30GB per movie), the reason I say this is because I have seen it happen, currently if a big disk copy happens, my music stutters, how would you configure this?

I could just have all my music on the 2TB but I would want a way of transparently syncing those files to the array.  It would be better if I could implement a tiered storage that moved music I was listening or a movie I was watching to over to the SSD, to read it from there, is it L2ARC, bcache, dm-cache, lvmcache, flashcache or something else, maybe if I use ZFS on the array I can only use L2ARC, does L2ARC do what I want, can I put L2ARC on the SSD with the OS?

EDIT: Oh and I'm thinking I may over-provision the 2TB by say 10%, good idea, I don't need the space, do I need to use windows for that or just create the partitions and leave 10% of the disk empty?

Thanks again for looking.

Richard

---

### Post by slickymaster on 2017-09-08
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2017-09-09
ZFS can be told about a hyper-fast cache and will use that.  

SMB/CIFS is slow compared to NFS or iSCSI or AoE, but it should be sufficient for any media files. High speed disks are not needed to handle any media streaming inside a home these days.  If you have stuttering issues, it isn't the disks.  Look at the motherboard or networking or disk connections. With all the RAM you have, ZFS will automatically cache things efficiently.  Even slow "green" drives are more than fast enough to stream bluray copies, BTW.

I do not know about thunderbolt or how it deals with queuing.  USB has issues with long queues which can make a disk effectively stall for 20+ seconds every few minutes on some hardware.  Queuing issues can be controlled by using 'nice' for any low priority tasks - like large copies.  BTW - use rsync for those.

If you use ZFS, don't use any non-ZFS caching methods.

Don't over-provision disks. Don't.

My media server is a $50 CPU on a $50 motherboard with 4G of RAM.  It manages 20+TB of storage and streams to 2 hidef playback devices concurrently without any issue.  It is not used for viewing, just as a pure data server either with NFS or Plex handling the streams.  It is also a Calibre server and does about 5 other tasks.  I've never had an issue with it (besides a failed disk).

I would strongly recommend that your backups be simple, outside RAID-anything.  When RAID goes wrong, having backups is sometimes the only way to recover.  Just search these forums for all the people who confused RAID with backups seeking help. RAID is never a replacement for backups. RAID solves 3 issues.  Backups solve 1001+ issues, including a failed RAID.

I cannot imagine on any system that audio could be impacted regardless of the file type on any current generation network, even wifi.

Lastly, don't use wifi networking for your server and avoid using it for any clients, especially with video streaming.  I'd rather see power-line ethernet uses than wifi. 

It will be interesting to read what others say about this too.

---

