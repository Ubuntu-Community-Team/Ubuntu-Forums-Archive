---
title: "Single user mode doesn't work!"
date: 2007-10-09
forum: Server Platforms
---

### Post by mogie on 2007-10-09
Hello peopl!

Have been trying to reset my root password in rescue mode with Ubuntu dapper LTS 6.06 server, and booth manually instert "single" to the endline of the kernel boot parameter. though - I only get withe the system has started:

"Give root password for maintance: (or press Control+D to continue)" where I need to insert my original passworrd which I ofcourse have forgotten..

Any advide? :)

---

### Post by MJN on 2007-10-09
There are probably more than one way to skin this cat, but I suggest:

1) Boot from a live CD (e.g. the Ubuntu install disk)
2) Create a mount point for whichever partition held /etc
3) Mount the partition
4) Open /etc/shadow from the mount for editing
5) Remove root's password (the long hash value $1$2b...etc from between the first and second colons) resulting in something like root::13492:0:99999:7:::
6) Reboot

Now root won't have a password so login without it and set a new one with [B]passwd

[/B]I haven't used the Ubuntu live CD in yonks but it could well be that it automatically mounts any Linux partitions it finds hence steps 2 and 3 above may well be unnecessary.

Mathew

---

