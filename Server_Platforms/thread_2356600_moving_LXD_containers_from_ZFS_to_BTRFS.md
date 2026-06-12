---
title: "moving LXD containers from ZFS to BTRFS"
date: 2017-03-24
forum: Server Platforms
---

### Post by courtney2 on 2017-03-24
I am very unimpressed with ZFS and also how confusing and messy it feels compared to BTRFS (primarily with using zfs send/receive to backup/restore my containers). Since I can get the same benefits I need out of BTRFS I want to switch. What I see though is that all my ZFS containers are a ZFS subvolume. Is there a way i can easily move these to BTRFS, or will I have to go inside my containers, backup the application contents and restore them to a new container on btrfs?

---

### Post by Tadaen_Sylvermane on 2017-03-24
I think you would have to rebuild the containers and move the data. Don't know enough to be sure though. I would stick it out with ZFS though. It is much more mature, BtRFS still has some issues as I understand it. Anything other than basic Raid 1 and 10 is unstable as hell and should only be used with throwaway data. I know when I have the cash I'll be upgrading my server with storage and I plan on using ZFS. My data to valuable to me to risk it on BtRFS.

---

### Post by courtney2 on 2017-03-25
I completely understand the concern with keeping data safe. I haven't had any issue using btrfs for 2 years, and everything is really considered stable at this point except RAID56, which they also call safe to use with the exception of power outages being able to corrupt data, otherwise RAID0,1,10 is safe. Though you are right, ZFS does have many more years under its belt. I'm really playing with backup solutions that provide the least downtime for running container services, and send/receiving snapshots is a total win. But like I said, I really dislike ZFS implementation of it. So messy to manage snapshots IMO. I have one more thing I want to try to see if I can stick on ZFS (or if there is something I am really missing with ZFS that makes backups easier), otherwise I'd be willing to rebuild my containers to switch everything to btrfs

---

