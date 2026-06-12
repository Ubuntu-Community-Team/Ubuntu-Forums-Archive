---
title: "iptables testing"
date: 2010-01-06
forum: Security
---

### Post by latev on 2010-01-06
just wondering if something similar is currently possible in iptables:

ideally a command which would simulate a packet flow and report what happened to the packet, for example

tcp packet from xxxxxx to xxxxxx 
traversed table 1
traversed table 2
....
dropped in table n

This would make debugging firewall rules a lot easier than doing temp logs in each table

---

### Post by Sarmacid on 2010-01-06
I'm not sure if that whole deal can be simulated, but it can actually be done with a little work. Just put up the first table and send a packet, and check the log, if it wasn't captured put up the second table, send the packet again and check the log. This could be done with scripting, but it would take a good while to write it.

---

