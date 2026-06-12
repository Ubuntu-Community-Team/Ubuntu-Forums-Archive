---
title: "pptpd, clients have no internet connectivity"
date: 2009-01-27
forum: Server Platforms
---

### Post by Kermos on 2009-01-27
I recently setup PPTPD on my ubuntu server for VPN.

I can connect with both windows and ubuntu clients no problem.

However, once connected, I have absolutely no internet connectivity from the client (connectivity is fine from server send).

I'm thinking that this is a routing problem, here is my route table from the client:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.0.1       192.168.72.1    255.255.255.255 UGH   0      0        0 eth0
192.168.72.9    0.0.0.0         255.255.255.255 UH    0      0        0 eth0
192.168.72.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

As you can see, ppp0 is 0.0.0.0 across the board and I have no idea why. Beginning to wonder if the fact that both my server and client being behind the same router might be the issue here.

The old servers are supposed to be replaced by this new server, but I can't make that switch until I know for a fact that everything works, hence the reason for the current setup like this.

Any ideas anyone?

Thanks!

---

