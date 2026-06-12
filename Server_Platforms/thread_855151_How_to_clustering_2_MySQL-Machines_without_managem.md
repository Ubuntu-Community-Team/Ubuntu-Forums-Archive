---
title: "How to clustering 2 MySQL-Machines without management node?"
date: 2008-07-10
forum: Server Platforms
---

### Post by mcfisch on 2008-07-10
I heard about the possibility of a mysql-cluster with 2 data nodes and one management node. But i only have 2 machines and have to install a high available mysql-server. our old (and slow) server runs on a master/slave-ha-cluster with heartbeat and drbd. But i'm afraid in losing performance when combining mysql with drbd. Which good ways else are there to realize this szenario?

Another idea: one of the webservers (heartbeat/drbd too) could take the management node role. And if the master dies, the slave would take the role together with its own IPs, Disks etc. :confused:

---

