---
title: "Source route at boot (/etc/network/interfaces ?)"
date: 2011-05-29
forum: Server Platforms
---

### Post by kihjin on 2011-05-29
I have a server with two IPs:

123.123.123.100
123.123.123.200

123.123.123.100 is the machine's fixed IP address. 

123.123.123.200 is a secondary address for which all traffic is handled by keepalived and forwarded to other systems.

**The problem:**

Outgoing connections use 123.123.123.200 as the source address, which causes the connection to fail, since received packets are forwarded at the layer 4 level. 

**The fix:**

sudo ip route change default via 123.123.123.1 dev eth0 src 123.123.123.100  metric 100

**The question:**

Is there some way I can configure this in /etc/network/interfaces ? I was thinking of using the 'up' command for the eth0:0 interface. 

Thanks

---

