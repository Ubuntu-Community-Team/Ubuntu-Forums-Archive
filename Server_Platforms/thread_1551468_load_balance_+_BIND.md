---
title: "load balance + BIND"
date: 2010-08-12
forum: Server Platforms
---

### Post by kendel on 2010-08-12
I started over combining the first parts of this guide: [[COLOR=#22229c]http://www.howtoforge.com/set-up-a-l...ter-ubuntu8.04[/COLOR]]("http://www.howtoforge.com/set-up-a-loadbalanced-ha-apache-cluster-ubuntu8.04") (Only the first few parts in terms of configuration and naming).

Then I used this guide: [[COLOR=#22229c]http://www.howtoforge.com/setting-up...n-debian-lenny[/COLOR]]("http://www.howtoforge.com/setting-up-a-high-availability-load-balancer-with-haproxy-heartbeat-on-debian-lenny")

Surprisingly enough all steps worked.
1. Now I need to set up LAMP servers with MySQL master/slave replication and Apache rsync.
2. Next i need to add BIND to both my Load Balancers with master/slave backup and replication...


Are there any guides to look at to follow on these? Can tou point me to the right direction for BIND with replication.

---

