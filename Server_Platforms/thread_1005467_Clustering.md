---
title: "Clustering"
date: 2008-12-08
forum: Server Platforms
---

### Post by kiminaiseah on 2008-12-08
hello everyone,

i have a little problem about clustering or this about redundancy..
i am planing to put some mirroring tool for my machines..
but still not clear in my mind what program or tool to be use for this..

the main idea is to replicate anything comes in server1 and when server1 goes down automatically the server2 which copies anything in server1 will comes up. 

what are the dependencias? do i need copy 1st everything that server1? or just put or install program which do all copying work.


thnks.

---

### Post by stiV on 2008-12-09
[http://www.linux-ha.org/](http://www.linux-ha.org/)

you could combine heartbeat and drbd for this purpose - many many tutorials out there ;)

---

