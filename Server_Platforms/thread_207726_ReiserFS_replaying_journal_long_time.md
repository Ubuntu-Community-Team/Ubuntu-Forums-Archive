---
title: "ReiserFS replaying journal *long time*"
date: 2006-07-02
forum: Server Platforms
---

### Post by quad3d@work on 2006-07-02
I just installed Dapper on my dual PIII 933MHz home server. I've noticed when replaying journal on my /home partition (biggest; 870GB) during boot takes a **LONG TIME**! Compared to Debian 3.1 install it takes 10X as long.

Even it said the filesystem is clean.. any thoughts? Thanks.

p.s. /etc/fstab noatime,notail options are applied to FSs.

---

### Post by GTvulse on 2006-07-02
Reiserfs is not a good choice of a slow(er) machine, nor a huge partition; unless you like to age while it replays the transation journal after a hard crash. If the size you mention is real, I would use JFS. I would use XFS only and only if your hardware is server-class with a high-quality UPS, not if it is commodity hardware; unless you like to have your files zeroed automatically after a hard crash (it is a feature, not a bug, btw).

---

