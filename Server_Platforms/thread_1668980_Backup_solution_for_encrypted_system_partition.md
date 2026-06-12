---
title: "Backup solution for encrypted system partition"
date: 2011-01-17
forum: Server Platforms
---

### Post by habrys on 2011-01-17
I have a little server running Ubuntu Server 10.04.1 LTS. There is a 250GB disk with system and some media files and a RAID5 matrix of 6x 1TB disks with media files. Both are encrypted. The system disk was encrypted during installation using Ubuntu built in mechanism.

I have another little server/NAS with a 750GB disk and Debian installed there. Both servers run 24/7.

I'd like to build a solution to automatically backup the 250GB system disk of the "big" server to the "small" one. It should run once a night over LAN and it should be possible to restore the system in case of failure also over network. I've read a bit about rsync etc., but I'm not sure if it suits my needs - because some non-standard requirements:
- the backup file should be a dump of the whole 250GB partition, which means it should also be encrypted,
- is an incremental setup possible under above condition?,
- if the server fails (won't boot up anymore, disk fails etc.), it should be possible to restore from the dump also over LAN (is it even possible? perhaps the system should be installed first after failure to get network running at least, right?).

I don't know... to put it simply... I lost the system twice in the last few years due to power outages. I bought UPS lately and it helps of course. But still I'd like to have an easy way to restore the system without installing and configuring it from scratch. And still, I don't want to backup files unencrypted- the whole point of encryption is lost then, right?

So what solution would you suggest? I just need a push in the right direction, no need of detailed solution :-)

---

