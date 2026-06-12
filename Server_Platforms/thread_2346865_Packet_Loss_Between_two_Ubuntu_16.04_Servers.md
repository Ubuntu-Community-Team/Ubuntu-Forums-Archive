---
title: "Packet Loss Between two Ubuntu 16.04 Servers"
date: 2016-12-19
forum: Server Platforms
---

### Post by streamingguy on 2016-12-19
We are experiencing packet loss between two Ubuntu Server 16.04 hosts that are on the same switch. When running mtr --tcp, we see packet loss starting around the sixth hop.


When going from a CentOS host to one of the Ubuntu hosts, we see no loss, only between the two Ubuntu hosts. The network configuration on all of the hosts is the default done by the installer.


We are at a loss with this, so any pointers with regards to resolving this issue are very much appreciated.

---

### Post by Graham_Willis on 2016-12-20
I'm not really a network guy, but do you mean that they're connected directly to the same switch? If yes, why are there six hops? I think that seeing this mtr output (disguised if needed) would be helpful.

What I can think of as possible causes for which packets are lost is firewall (e.g a limit of how much data can be transmitted in a given time interval) or a bad cable. Or perhaps you have a network loop?

---

### Post by streamingguy on 2016-12-22
Sorry for the confusion, we start seeing packet loss after the 6th packet is sent. There is only one hop.

There is no firewall on these servers or at the network level. There is no network loop.

ubuntu (0.0.0.0)                                       Thu Dec 22 16:36:24 2016
Resolver: Received error response 2. (server failure)er of fields   quit
                                       Packets               Pings
 Host                                Loss%   Snt   Last   Avg  Best  Wrst StDev
 1. hidden                    12.5%     8  2002. 1395. 200.9 2002. 732.4

---

### Post by Graham_Willis on 2016-12-27
Bad cable? Bad port? A cable which is not appropriately inserted into the switch's port?
Try to swap the machine which is connected to this port with another, properly functioning one and see what will happen.

---

