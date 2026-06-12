---
title: "raid + S30checkfs.sh gives me problems"
date: 2007-01-22
forum: Server Platforms
---

### Post by stratos_v2 on 2007-01-22
I'm setting up a ubuntu based server (based on ubuntu server release 6.10 ) but am having some problems.

I've partitioned 2 disks approximately as followed:
25 MB /boot ext3
5 GB /tmp RAID ext3
50 GB /var RAID ext3
175 GB / RAID ext3
2 GB swap

and the other disk exactly the same, with the first partition not tagged as /boot of course. (but will be used to duplicate /boot anyway.

imho, a pretty common setup?

however when i boot up the server,
it will correctly initialise md1,2,3 (or 0,1,2 can't recall)
and will start booting correctly, then when it starts S30checkfs.sh it failes when it tries to check sda3 (which is of course busy being in raid)

Now i can hardcode S30checkfs.sh to only check the correct partitions, but i'm guessing that will result in a maintenance nightmare every time the init scripts get updated because i will have to find out what changed and change this myself.

A much better way would be to find out how it decides what partitions to check.
If anyone knows please share, or if you think there is something else wrong also please say so.
Because if this got tested (and i can't imagine that it hasn't) this would have been spotted i think.

---

### Post by stratos_v2 on 2007-01-24
So is there anyone who remotly can guess what might be the problem?

I'll even go for people whom are also running raid to tell me that it's working fine for them.

---

