---
title: "system failover using rsync"
date: 2009-03-11
forum: Security
---

### Post by darint on 2009-03-11
I am looking for a guide specific to using rsync for complete server replication to a partition on a second server.  The second server would be used for other non-critical operations and then booted to the other partition (the one containing the rsynced image) should a failure occur.

---

### Post by HermanAB on 2009-03-11
The heartbeat project is what you are looking for:
[http://www.linux-ha.org/](http://www.linux-ha.org/)

Cheers,

Herman

---

