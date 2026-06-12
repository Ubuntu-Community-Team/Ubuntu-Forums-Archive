---
title: "MySql Slow Query log and NFS"
date: 2011-12-05
forum: Server Platforms
---

### Post by jumpjumpholydiver on 2011-12-05
We're currently running MySQL 5.1.6 on Ubuntu 10.04 server.  I'm trying  to write my slow query log to an NFS mount, but I keep getting an Error  13 - " 17:08:34 [ERROR] Could not use /var/log/mysql/querylogs/10.5.0.32/slowquery/slow.log for logging (error 13)"  The mount is at the "querylogs" directory and  appears to be fully read/writable on the server, but for some reason  MySql cannot use it.  Does anyone have any idea what may be causing  this? I tried changing the permissions on "querylogs" to be the same as the  rest of the MySQL logs (error, etc.), but no dice.  
Also...the NFS mount I'm accessing is on a NetApp SAN.
Has anyone else here seen this? Any help would be greatly appreciated.
Thanks!
A

---

