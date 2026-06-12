---
title: "buying a new server need input"
date: 2008-03-20
forum: Server Platforms
---

### Post by BillGod on 2008-03-20
We are setting up a new mysql cluster.  We would like to purchase some dual processor quad core servers.  I cannot find any information that says ubuntu will take full advantage of the dual quad cores.  From what I read I see that it will "see them and use them" but does it take full advantage of them.  I mean is it worth the extra $ for the quad cores or should I just stick to dual core?

---

### Post by craigp84 on 2008-03-21
The problem's not Linux, but mysql. The Linux kernel will efficiently use all 8 cores. However MySQL wont. 4 cores is the magic number for mysql.After that, it's severely diminishing returns, i.e. there's little point.

Postgresql, or if you're prepared to pay a couple of quid, Sybase, will take full advantage of the 8 cores.

Google, there's tons of analysis already out there in terms of MySQL performance across X CPUs.

A good way to get the 8 cpu performance from MySQL would be to setup replication. Having a "reporting server" is a common approach -- it's a read only replica and all the read only processes acess that instance, and the processes which do updates go to the master.

You can also have multi-master replication, but to do that properly involves some understanding both on your part, and more so on the programmer's part!

-c

-c

---

### Post by BillGod on 2008-03-21
thanks craig that helps a ton!

---

