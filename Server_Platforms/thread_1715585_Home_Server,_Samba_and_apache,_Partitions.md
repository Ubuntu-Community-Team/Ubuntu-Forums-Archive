---
title: "Home Server, Samba and apache, Partitions?"
date: 2011-03-27
forum: Server Platforms
---

### Post by GiSWiG on 2011-03-27
First, my searching hasn't found exactly what I'm looking for. If this is redundant, please point me to link.

Setting up a small home server. Planning to have apache and samba. I have 2 80Gs for RAID1 for main system and 2 250Gs for RAID1 samba. Going to use LVM and adjust as needed.

I'm still learning on the server side of this. Experienced on desktop side. 

So here's what I'm thinking...
/dev/sda 
  /dev/md0 - /boot - 256M
  /dev/md1 - /swap - 2G
  /dev/md3 - lvm - rest of drive
    vg0/lv0 - / - 10GB
**  vg0/lv1 - /var/log - 3G** 
  vg0/lv2 - /home - 5G
  vg0/lv3 - /srv - Rest of disk 
    /srv/www - linked from /var/www (or defined in smb.cfg)
    /srv/minecraft - :-)

/dev/sdb
 /dev/md0
  vg1/lv0
    /srv/samba - whole drive

ext4 will be used for all partitions

I bolded the /var/log cause I'm not sure just how big to start with a home server just doing samba and apache (minecraft is irrelevant). Eventually, apache will be a user/pass protected web server for family pics to distant relatives. I expect it won't be as big as partitioned here.

**So, how big should I consider for /var/log? **

I know of logrotate to help control it and LVM to help as well.

Thanks!

---

### Post by kidders on 2011-03-28
Hi there,

I'm curious... Why have you chosen to put /var/log in a partition of its own? The only reasons I can think of are ...[LIST]
[*]You plan on creating & rotating so many logs so rapidly that your root filesystem would fragment wildly if you didn't. That doesn't seem very likely on a home server though.
[*]You want to use a filesystem type other than that in use on your root filesystem. Again, that doesn't apply to you.
[/LIST]

Anyhow, to answer your question, I'd suggest something in the region of a couple of hundred megabytes for the partition. Anything even *close* to a gigabyte seems way too large, imo. (I can't imagine there being much benefit in retaining lots of log data on a home server.)

I hope that helps.


[SIZE="1"]_Off Topic_
I was just wondering whether you should put your swap on RAID 1. Similar to /var/log, I can't think of a reason for doing it that applies to a home server. I can imagine, for example, that someone running a mission-critical service might suffer the performance hit in exchange for the reassurance that a hardware failure under a swap filesystem wouldn't destabilise the system. You, on the other hand, might get more benefit from using the same disk space for two parallel swap filesystems, rather than a single, mirrored one.
[/SIZE]

---

### Post by GiSWiG on 2011-03-28
Yeah, it has. Running desktops is one thing, servers are another. I've done enough Windows servers and it's straight forward. C:\ and [DEFG--Z]:\ for everything else. I still have to slap some people around cause they think 10GB for C:\ is fine. Then put them in the corner of the server room, kneeling with nose touching the corner (well, I would like to).

I think I'll just go / @ 15GB, /home @ 5GB and the rest for /var/www, with /var/samba on other drive. Minecraft won't ever take all that much so I'll just put it in /var (on the / partition) or /home (not sure).

---

