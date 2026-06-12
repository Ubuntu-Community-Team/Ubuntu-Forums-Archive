---
title: "Random cpu usage"
date: 2009-09-10
forum: Server Platforms
---

### Post by MasterChief on 2009-09-10
I have an HP ProLiant DL580 G2 with quad 2.2ghz MP Xeons and 8gb of ram.

Ubuntu server 9.04 32 bit is installed along with Apache, PHP, SSH server, MySQL, and PHPmyadmin.

System monitor shows all 8 cpu's and 7.6gb of ram with currently 190mb of ram being used. Almost all processes are asleep or idle as we are just setting things up for it to be a game server. 

I'm seeing one or two cpu's being run at 100% with the load switching between two cpu's. First it was between cpu 1 & cpu5. Now after a reboot it's using cpu2 & cpu6. It seems to be moving around...but i can;t figure out what is causing this kind of load with nothing basicl running?

Any ideas or thoughts would be useful. Thanks

---

### Post by nandemonai on 2009-09-10
> **MasterChief said:**
> I have an HP ProLiant DL580 G2 with quad 2.2ghz MP Xeons and 8gb of ram.

Ubuntu server 9.04 32 bit is installed along with Apache, PHP, SSH server, MySQL, and PHPmyadmin.

System monitor shows all 8 cpu's and 7.6gb of ram with currently 190mb of ram being used. Almost all processes are asleep or idle as we are just setting things up for it to be a game server. 

I'm seeing one or two cpu's being run at 100% with the load switching between two cpu's. First it was between cpu 1 & cpu5. Now after a reboot it's using cpu2 & cpu6. It seems to be moving around...but i can;t figure out what is causing this kind of load with nothing basicl running?

Any ideas or thoughts would be useful. Thanks

Tried checking out top / htop / ps -A etc?

There is probably some binary doing something around there somewhere. ;)

---

### Post by MasterChief on 2009-09-11
Thanks for the reply. I'm new to Ubuntu so might be stumbling around for awhile.:)

---

