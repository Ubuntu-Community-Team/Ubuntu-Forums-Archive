---
title: "Network goes down after a few minutes"
date: 2012-03-14
forum: Server Platforms
---

### Post by om06zr on 2012-03-14
I have a server which I've been using at home (with no problems) for about a year. I recently upgraded the memory from 2x2GB to 2x4GB and updated the operating system to ubuntu server 11.10. Following this I have network problems with the server after a few minutes. For example, if I log in immediately after power up and run ping, I get the following output

$ ping 10.1.1.1
64 bytes from 10.1.1.1: icmp_req=1 ttl=64 time=0.516 ms
...
64 bytes from 10.1.1.1: icmp_req=46 ttl=64 time=0.488 ms
64 bytes from 10.1.1.1: icmp_req=47 ttl=64 time=23789 ms
from 10.1.1.11 icmp_seq=123 Destination Host Unreachable
from 10.1.1.11 icmp_seq=129 Destination Host Unreachable

where 10.1.1.1 is my home router. All the other computers on the network are fine so the problem seems to be with the server. I've tried searching around for a fix but I've yet to find anything helpful. Part of the problem is that I'm not sure what could cause such behaviour. Does anyone have any ideas? Thanks :)

---

