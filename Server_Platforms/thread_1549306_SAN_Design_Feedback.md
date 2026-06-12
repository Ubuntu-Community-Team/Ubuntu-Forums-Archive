---
title: "SAN Design Feedback"
date: 2010-08-09
forum: Server Platforms
---

### Post by nmp0906 on 2010-08-09
I am looking to accomplish the task of building a budget SAN. Its first use will be as an archive/backup solution, but hopefully in time I can stabilize and tune the configuration to be used for more important / critical tasks.

My current working design follows a NetApp setup with filer "heads" and disk "shelves". In reality, each are separate servers with specific tasks.

The disk shelves are 12-16 SATA HotSwap servers loaded with 1.5TB drives. I want to make these iSCSI targets. I am still debating whether to do hardware/software RAID at this level or export each disk individually.

The filer head would map these iSCSI targets via the iSCSI initiator and aggregate these in a fault tolerant way to present combined storage that can be served up via any number of protocols (NFS for *nix boxes, CIFS for Windows, etc).

I need to also make the filer heads redundant / highly available. If one fails, the other takes over (eventually this needs to be seamless to the hosts, ie. they don't have to remount the share). Disk shelves are already redundant in the fact that there is some sense of RAID applied across them.

The goal is to be able to add shelves and aggregate the extra storage as needed. ZFS (available with FreeNAS) is really intriguing in this regard.

I am evaluating OpenFiler and FreeNAS. Do you have any thoughts, opinions, or comments on accomplishing this? I realize it's possible to set this up manually using Linux or BSD on each, but either OpenFiler or FreeNAS would make this extremely easy for initial setup and ongoing support (even for the Windows admins).

Thanks.

---

### Post by rubylaser on 2010-08-09
Although ZFS is cool, I personally wouldn't ever use it because you can't add disks to an existing array.  You'd have to append a new array onto your existing on.  This stinks if you ever plan on expanding your disk count.

I personally would Use GlusterFS or DRDB/Heartbeat to setup a fault tolerant system.  What it sounds like to me is that you want to build a budget NAS more than a SAN.  If that's the case Openfiler or FreeNAS will both work fine. I've tried both and I prefer Openfiler's more polished GUI.  That being said, I always roll my own storage.

---

### Post by nmp0906 on 2010-08-09
What I'd really like is to be able to add more storage servers on the fly and grow the available pool of storage.  In doing this, I'd like to tolerate one or more storage server failures (similar to a RAID set).

My original thought process was to have storage servers export their disks over iSCSI or AoE and a clustered pair of boxes would handle the software RAID over these exports and turn around and server CIFS/SMB and NFS to clients.

Are either OpenFiler or FreeNAS able to be utilized in this manner?  Or should I be looking to roll my own custom configured box?  I've started reading into high availability samba setups which looks fairly intricate from a configuration perspective, something that wouldn't be able to be configured graphically anyways.

Any personal experiences with GlusterFS?  I read about it awhile back, but haven't eval'd yet.

---

### Post by rubylaser on 2010-08-09
Yes, GlusterFS works well, my brother uses it for storing network traffic monitoring info(datacenter). MogileFS maybe another option as well [http://www.danga.com/mogilefs/]("http://www.danga.com/mogilefs/").

---

