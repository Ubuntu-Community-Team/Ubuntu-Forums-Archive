---
title: "Server 10.04: no boot: ureadahead-other main process"
date: 2010-06-18
forum: Server Platforms
---

### Post by trinix007 on 2010-06-18
[FONT=Verdana]Hi all,

I tried to freshly install a ubuntu server 10.4 32bit version on my Foxconn R10-S1 barebone (2x500GB, 1GB RAM).

When I boot, the machine hangs with following message.

[/FONT]init: ureadahead-other main process (751) terminated with status 4and nothing happens more.


I did carry out the followng config during installation:

[LIST]
[*]2 HDD with 3 primary partitions each to RAID 1 (\boot, swap, LVM)
[*]LVM includes 1 Volume-Group with 2 logical volumens ("root" with  mount point \, "var" mit mount point \var)
[/LIST]

I am quite new to this subject! How could I resolve that problem and get the server running?


Thanks in advance,
Christian

---

### Post by sjinks on 2010-06-19
As for the readahead, they say [it's not a bug, it's just a harmless warning]("https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677").

Could you please remove "quiet" option from the kernel command line? You will probably see more info as to why the system fails to boot.

---

