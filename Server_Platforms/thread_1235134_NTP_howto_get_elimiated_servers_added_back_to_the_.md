---
title: "NTP howto get elimiated servers added back to the pool?"
date: 2009-08-08
forum: Server Platforms
---

### Post by hanasaki on 2009-08-08
There is a corporate firewall running Ubuntu and the NTP server.  This is the master for the entire company and it has a list of several servers on the Internet from which it will get time updates.  All of the internal computers (windows and linux) sync to this master.  It seems that sometimes the firewall NTP server we run sometimes looses contact with the Internet server it is syncing from and automatically removes this external server from the list of external servers that are consulted.  Eliminated servers are never retried and thus eventually the the firewall NTP server has not servers to sync with (all eliminated) and therefore it, and the internal client computers, all goto stratum 16 and there are "no suitable servers for synchronization"  

**How can NTP server be configured to readd eliminated servers to the the pool and "heal" itself?  both on the firewall and the internal clients?**

**What NTP client only program is a good deamon to run on both windows and linux computers (ex: desktops and datacenter servers)?  Or is it best to not install a daemon and just use  a chron job with ntpdate 'timehost" ?   **It is important that the client computers and desktops NOT be a NTP server - only client.  The NTP server package appears to only function as both without any way to configure it not to server time.

TIA

---

