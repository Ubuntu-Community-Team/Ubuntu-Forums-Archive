---
title: "Auto Data Mirroring across servers"
date: 2018-06-29
forum: Server Platforms
---

### Post by mcapaldo on 2018-06-29
I have been doing some upgrading on my home pcs/Lan.  I am bulding a 2nd ubuntu server as a redundancy.  Just got a managed 10/100/100/10gb switch with 4 SFP+ ports.  So the servers will have !0GB nic speeds.  (got 10GB Cards installed( in them).      

 Home Server #1: PC running ubuntu server 16.04 with 6x2tb drives running mdadm RAID5 (soon to be RAID6) CPU AMD 6000+ Ram 2GB Boot OS is 64GB SSD un External Case via USB 2 Port Gigabit Nic & 10GB 2 port Nic       

 Home Server #2: PC Running ubuntu server 16.04 with 4x6tb drives running mdadm RAID6.  I want to ultimately update the 2tb drives one at a time to 6TB each, then increase the array AFTER home server #2 is setup right and running well for a while. Fx-8350 8GB Ram Boot OS is 64GB SSD un External Case via USB 2 Port Gigabit Nic & 10GB 2 port Nic      

  I have a Media Server PC with 2x6TB RAID1, and 2x3tb RAID1 also but that is not an issue now.   

       Luckily I have my notes from the 1st time I setup Home Server #1.  Basic Core server install with mdadm, & Samba  So I have the home server #2 so it boots and auto mounts the new 4x6tb raid6, no problems.  

  My question is besides running rsync to replicate data that way via cron jobs throughout the day, is there a better way?      So if I do a client workstation backup to Home Server #1 it also goes to Home Server #2 automatically without a 2nd rsync command to Homesrever #2 from client machines.  I supposed I could write a script to rsync to home server #1 then to run again to Server #2.    There has to be a better way, and the simpler the better.

---

### Post by lisati on 2018-06-29
Moved to *Server Platforms* for a better fit.

---

### Post by TheFu on 2018-06-30
With all that storage, seems like you need ZFS and would want to use the snapshot tool to replicate between the different systems.
RAIDz and RAIDz2 will change your life.

I have used rsync as you said - 1 direction then the other.  Once in a while, things get out of sync and data loss can happen.

Another option is to use storage clustering. Gluster is the normal answer, but I've been playing with sheepdog and like it.  I'm not ready to put any production onto it and it does have some caveats for use, but those aren't bad for my needs.

But with all this talk of RAID, we should probably mention for lurkers that sometimes RAID issues come up and the only fix is to wipe the array and start over from ... wait for it ....









[CENTER]backups.[/CENTER] 

Always have backups for data you can't afford to loose.  RAID solves 3 issues.  Backups solve 1001 issues.

---

### Post by LHammonds on 2018-07-02
> **mcapaldo said:**
> I am building a 2nd Ubuntu server as a redundancy.

> **mcapaldo said:**
> My question is besides running rsync to replicate data that way via cron jobs throughout the day, is there a better way?

There are many different ways to provide additional stability of your service but you need to be absolutely clear in what you are trying to achieve.  If you have a media server, it likely includes a database that needs to be replicated besides just keeping media file shares in sync.

Are you talking about redundancy in terms of server #2 being online and ready to take over for server #1 if it fails (e.g. goes dark)?  Like replication and failover using a heartbeat.

Or are you talking about server #2 being a backup of server #1 so that if #1 fails, you have a server you can transform to act like #1?  Like a backup repository with timed snapshots to provide disaster recovery if server #1 has data corruption.

Or are you talking about server #2 providing additional scalability so that both server #1 and #2 are providing the same service to the client machines at the same time to decrease bottleneck workload of the server/data path?

LHammonds

---

### Post by mcapaldo on 2018-08-08
I ultimately chose to build a new ubuntu server 16.04 lts 64 bit machine with mdadm RAID6 and samba.  It was easier on the clients to make a few extra empty directories in the /mnt folder.  and modify /etc/fstab (after samba was fine tuned on the server).  Then one character addition to the existing rsync command and now i have 2 ubuntu servers to backup to.  Both go on and then rsync backups to each machine separately.   And the old server data thruput was 70-85 MB/Sec on server #1, and now its 107-115 MB/Sec on new machine.  All on a unmanaged gigabit  network.    Server #1 - Ubuntu 14.04 LTS AMD x2 600 CPU 2.4GHz Dual Core 6x2tb drives all sata 2  Server #2 - Ubuntu 16.04 LTS AMD 8350 CPU 4.0GHz Eight Core 3x6tb drives all sata 6  I chose to Keep It Simple.  No Zpools, no LVM, just mdadm and samba.    Thanks for all the advice everyone.

---

