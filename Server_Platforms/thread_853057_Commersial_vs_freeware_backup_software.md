---
title: "Commersial vs freeware backup software"
date: 2008-07-08
forum: Server Platforms
---

### Post by qrwe on 2008-07-08
Hello,

I work at a comapny that recently needed a backup solution for all of their servers. Soon after, we purchased license of Puredisk to make some tests and try-outs. Sadly, Symantec (who is the distributor of Puredisk) wants outrageous **$12500** for a terabyte backup license!
This made me think a little. Maybe there is a freeware solution that could compete with Puredisk. Has anyone of you any experience with Puredisk vs Bacula (or similar)? Any comments are welcome.
Regards!

---

### Post by horeon on 2008-07-08
Hi,

I don't know Puredisk and read about Bacula, it's very interresting but it seems you need to install a client agent on each server... 

I have some servers and use backuppc (with some pre-scripts to manage sql backups,... ) to backup them with a dedicated networdcard on each.
It work perfectly, no need client agent. Have a web interface, to restore them and manage your backup by user with authentification, really fast restore...

Maybe it's enought for you :) [http://backuppc.sourceforge.net/](http://backuppc.sourceforge.net/)

Franck

---

### Post by windependence on 2008-07-08
bacula or Amanda.

-Tim

---

### Post by lamego on 2008-07-08
It would help if you could describe your backup requirements...

---

### Post by qrwe on 2008-07-10
Sure:
* It should be able to reach all sorts of network protocols/network files systems, such as samba. It's mostly Windows servers.
* If it's possible, it should be able to backup SQL databases.
* Backups need to be incremental: a first full backup, followed by changed files each day.
* Some GUI, such as web interface, is appreciated (and often mandatory these days).

---

