---
title: "Unable to reach Ubuntu Server with hostname"
date: 2011-08-14
forum: Server Platforms
---

### Post by crotale on 2011-08-14
One of my Ubuntu servers has stopped answering to its hostname from other computers on the LAN and I'm looking for some pointers on what and how to get it working again.

The network:
- m0n0wall router/gateway, acts as DHCP server aswell, IP x.x.x.1
- Ubuntu Server 10.04.3, "serverA", WINS server, printer server, etc., IP x.x.x.2
- Ubuntu Server 10.04.3, "serverB", storage, wed dev, etc., IP x.x.x.3

and a couple of desktop and laptop client running W7 and XP.

I have always been able to reach both Ubuntu server from the Windows machines
with either "\\x.x.x.x" or "\\serverA" but the latter has now stopped working on the 
"serverA" machine.

Two W7 machines have the printer mapped to "\\serverA" and it has stopped working.
From either of the W7 machines, pinging the IPs works well and "serverB", but not "serverA".

I have no real idea on where to start looking. Any suggestions are welcomed.

---

