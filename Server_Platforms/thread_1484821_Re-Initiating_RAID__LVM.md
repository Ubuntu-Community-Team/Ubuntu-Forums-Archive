---
title: "Re-Initiating RAID / LVM"
date: 2010-05-16
forum: Server Platforms
---

### Post by cadriel on 2010-05-16
Hi all,

I'm currently running OpenFiler. This has served me well in the past, but recently my requirements have changed. Initially this was the requirement to support Mac based systems - and then the requirement to run my torrent needs. Along with that came broadcatching - and you get the idea. OpenFiler makes installing these requirements quite difficult - although I've managed to accomplish most of what I need, the most important for me was the OSX support - specifically being TimeMachine backups.

Ubuntu 10.04 server seems to fit my needs - and I've been running a virtual box VM of it for a while to get accustomed to things. Netatalk covers off my time machine requirements - and i'm quite comfortable getting my rtorrent / rutorrent combination running.

My question is, OpenFiler has setup my data partition as a RAID 5 (4 x 1TB) with LVM over the top.

Will Ubuntu see this - do I need to note down configuration of the RAID 5 / LVM setup? If so - what in particular?

Also - am I able to test this using the LiveCD for example, before I go ahead with a new install? What example commands would I need to mount the raid and LV in order to check it?

Also - I think OF set the partition up as XPS - can you convert the parition to EXT4, should I even consider this or leave it?

The reason I ask is I want to be sure that I won't lose the data on my RAID BEFORE I go ahead with a new install ;)

The system partitions are on a 5th separate disk - the RAID 5 is purely for the data storage.

Thanks ahead for any help! :)

--
Craig.

---

