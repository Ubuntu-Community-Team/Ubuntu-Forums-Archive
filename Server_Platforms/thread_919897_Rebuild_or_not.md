---
title: "Rebuild or not"
date: 2008-09-14
forum: Server Platforms
---

### Post by JanvL on 2008-09-14
Hello,

The situation I found:

I am confronted with a SME-Server that was administered by someone that left NO documentation whatsoever. I found 3 servers, 1 with ICOP, second with SQUID/backup and the third a SME-Server in 19-inch rack producing a lot of warmth. All behind a router with its own firewall!

What were they used for? Filesharing for 5 PC's with Windows XP and about 35 Gb of Data, mainly office stuff and some (private) photo's.

Now my problem is that I want to dismantle the SME-Server and build up a Ubuntu/Debian fileserver with Samba. Documented this time. But the system was build on a software-raid with 2 pieces 500 Gb sata HD's that are not partitioned in an orderly way. So I guess I need them re-partitioned hopefully without dataloss, . After that I would like to install Ubuntu/Debian on another partition and put (copy) the data on yet another partition.

The backup-server has only got 1 piece 60 Gb HD, that is where the backupdata is stored (not on the raid!)

The SME-Server even has got a tape-unit that is not used!

I figured out how to disable the software-raid. A hardware-raid is no option with this hardware.


I need some suggestions before I start please . . . 

Is it right to dismantle the SME-Server? The owner cannot administer any server.
Making only 1 Server with (sw-raid) mirrored disks, and tape-backup a good idea?

I would be happy with any kind of feedback!

Thanks in advance,
Jan

---

