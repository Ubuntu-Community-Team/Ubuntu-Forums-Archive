---
title: "SNMP traps from specific device?"
date: 2013-03-04
forum: Server Platforms
---

### Post by GodAtum on 2013-03-04
At the moment I have the snmptrapd.conf file set up to forward traps from a cisco switch to a 3rd party server like so:

forward <oid> <server ip port>

Is there a way to filter the oids for particular device as I only want traps generated for specific device. Something like this:

forward <device IP> <oid> <server IP port>

---

