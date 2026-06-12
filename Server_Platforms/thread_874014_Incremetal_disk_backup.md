---
title: "Incremetal disk backup"
date: 2008-07-29
forum: Server Platforms
---

### Post by mogie on 2008-07-29
I need to copy (incremetal backup) my sdb disk to hdc, about 0400 O'clock at night. Both disks are 200.0GB, but not the same so I'm a little bit sceptical to go through a whole mirroring process with RAID 1. So for now I want to just easily copy all changed files from sdb to hdc at night.

Any recipe? :)

oh.. and I the partition table is the same on both drives already. They both have the three /,/boot and /home partitions which I want to copy.

---

### Post by hyper_ch on 2008-07-29
if you want to copy/sync files, use rsync

---

### Post by amenszer on 2008-07-29
If you're goal is to achieve a mirrored drive, RAID is definitely the best way to go...but you can also use dd.
Here's a page on that:
[http://www.debianhelp.co.uk/ddcommand.htm]("http://www.debianhelp.co.uk/ddcommand.htm")

But if you're just backing up data...
This can be accomplished with rsync and cron. 

Basically, setup a cron job in the cron.daily directory (you may need to adjust /etc/crontab so cron.daily runs at 0400) that rsyncs data from one drive to the other. This way, the only things that are copied over every night are new files and files that have been altered.

---

### Post by mogie on 2008-07-30
ended up using this one :)

[http://www.seismo.ethz.ch/linux/rsync.html](http://www.seismo.ethz.ch/linux/rsync.html)

---

### Post by hyper_ch on 2008-07-30
rsync is very straight forward but very powerful :)

---

