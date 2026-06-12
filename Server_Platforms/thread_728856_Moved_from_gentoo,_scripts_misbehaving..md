---
title: "Moved from gentoo, scripts misbehaving."
date: 2008-03-19
forum: Server Platforms
---

### Post by mortexic on 2008-03-19
I know this post is going to be a little light on tech details, but please believe that I'm not a totally clueless noob, and I -have- been doing this for about twelve years now (unix/linux in general)

That being said, here's the situation:
We had a server running some backup scripts running on gentoo. Due to a failure im unable to explain, one of the scripts rsync'ed over / instead of /path/to/backup/storage and the system was unbootable .. . so I had to get things up quickly so I installed ubuntu server 7.10 over the gentoo install (all data and scripts were/are on seperate partitions/drives)

What I had:
32bit gentoo on x86 hardware
vixie-cron
bash
rsync
gzip
syslog-ng

What Ive got now:
32bit Ubuntu server 7.10 on x86 hardware
apt-get smbfs 
ubuntu's default cron (?)
ubuntu's default logger

Behavior I'd like to recreate but am not sure how:
The output of the scripts-via-vixiecron was emailed to me every night on gentoo by default. I'm not sure how it was happening, gentoo's default MTA is ssmtp. 

What Im seeing:
The scripts are definately running at-all, I see stuff in /var/log/syslog to indicate it .. but it seems they are failing without error .. the amount of data being copied is incomplete and many files are missing (plenty of storage space) without any errors logged or anything.

So my question:
What am I missing? Is the parsing of scripts so radically different in ubuntu? Is ubuntu's cron executing them with ksh rather then bash or something? 

Here's an example of two of the scripts that arent running as expected:
(ips replaced with xxx)

```
date
echo "cd /storage/b/fileserver"
cd /storage/b/fileserver
echo "----"
echo "rsync -av --stats --delete rsync://xxx./var ./var"
rsync -av --stats --delete --ignore-errors rsync://xxx/var ./var
echo "----"
echo "rsync -av --stats --delete rsync://xxx/etc ./etc"
rsync -av --stats --delete --ignore-errors rsync://xxx/etc ./etc
echo "----"
echo "rsync -av --stats --delete rsync://xxx/share1 ./share1"
rsync -av --stats --delete --ignore-errors rsync://xxx/share1 ./share1
echo "----"
echo "rsync -av --stats --delete rsync://xxx/share2 ./share2"
rsync -av --stats --delete --ignore-errors rsync://xxx/share2 ./share2
echo "----"
date
date > /storage/log/last-fileserver-backup
```

It stopped halfway through /share1, the drive was not out of room.


Anyone have any thoughts? I'm at a loss here...

---

