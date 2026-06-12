---
title: "PPTP to Windows problem"
date: 2012-03-31
forum: Server Platforms
---

### Post by Russianeer on 2012-03-31
So I install PPTP server, configure everything, assign a local ip, remote ips, start it and connect to it from my windows machine. It connects just fine using the username and password I configured. But, once I connect to the VPN, I can not connect to anything else. I can't even ping google, but I can still connect to the actual server that's hosting the VPN. And if I type ipconfig and look at the IP that the VPN assigned to me, it appears to be one of the IP addresses that I assigned with the remoteip config.

Could anyone point out what the problem could be?

---

### Post by Russianeer on 2012-03-31
Fixed. Had to run this line in iptables.

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

---

