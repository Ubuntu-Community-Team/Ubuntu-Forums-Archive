---
title: "bind question"
date: 2012-03-08
forum: Server Platforms
---

### Post by Drenriza on 2012-03-08
Hi all.
 
Im having a small school project (9 days long) where i have been asked to fit a bind server into my network.
 
My question is as follows. Can bind be used in a way, so i can say (on a host machine) ping server1 and the host / client ask the bind service (which is on another server, for example server3) who is server1 and get an ip address returned it can ping, from the bind service.
 
So i from any host (without manually configuring the hosts file) can say ping a server (by name) and it gets the ip from the bind service.
 
Thanks on advance.
kind regards.

---

### Post by Cheesemill on 2012-03-08
Yes it can.

That is exactly what bind (or any other DNS server) is for.

---

