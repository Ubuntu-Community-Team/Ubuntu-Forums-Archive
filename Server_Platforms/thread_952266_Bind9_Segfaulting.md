---
title: "Bind9 Segfaulting"
date: 2008-10-18
forum: Server Platforms
---

### Post by spauldingsmails on 2008-10-18
Hi

I have a strange problem that has only recently started (i.e. in the past day or so) where about every 12 hours my Bind9 server stops with the following error;

Oct 19 11:29:00 czervik kernel: [3772258.194120] named[16716]: segfault at dededede eip b7ce4274 esp b7283130 error 4

I was thinking perhaps there is a problem with the machine but all other daemons on the machine are running fine; Apache, MySQL, etc.

I have made no changes to the named scripts for a couple of months and have not had any issues with the server (hardware or software) since I installed Ubuntu 8.04 Server about 5 months ago.

Also, is there some way I can get bind to log more errors? This may lead to a clearer answer to the problem I'm experiencing.

---

