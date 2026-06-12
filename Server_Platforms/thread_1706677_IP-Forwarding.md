---
title: "IP-Forwarding"
date: 2011-03-14
forum: Server Platforms
---

### Post by abfalleimer on 2011-03-14
Hello,

since I upgraded from Ubuntu Server 8.04 LTS to 10.04 LTS I am facing the following problem: I am using different VLANs e.g. VLAN1 and VLAN2 as well as a normal subnet ETH0. My workstation has an IP in VLAN1. With 8.04 LTS I can ping the server's address bound to ETH0 (let's say 192.168.1.2) from my machine (let's say 192.168.2.3), even if the server's interface VLAN1 (with address 192.168.2.2) is up. The requests arrive at ETH0 and the replies leave at VLAN1 (as seen with tcpdump). But with Ubuntu 10.04 the requests arrive at ETH0 and then nothing happens. I can not see any reply at any interface.
This leads to problems with ssh as the vlan-interfaces are not allways up so I usually have to connect to the address bound to ETH0. But when I bring up VLAN1, the connection goes lost.
The value of /proc/sys/net/ipv4/ip_forward is 0 on both machines.

any idea what may be different?

---

