---
title: "VPN server IPsec/L2TP without router"
date: 2009-11-12
forum: Server Platforms
---

### Post by molgan on 2009-11-12
I'm trying to install a IPsec/L2TP-VPN server on my ubuntu 9.04 server.
I read that PPTP was unsafe and OpenVPN needs additional applicaton to work under win xp.  Then it seems that IPsec/L2TP is the best alternative.

I've read some tutorials about this, but I've just found tutorials where the server is behind a router, which isn't my case.
My server is directly connected to the internet with a static IP-address.

So I've found out that you need the packets openswan & xl2tp.

[This guide]("http://rootmanager.com/ubuntu-ipsec-l2tp-windows-domain-auth/setting-up-openswan-xl2tpd-with-native-windows-clients.html") tells us to type the password directly into a textfile. I thought logging in thru the server's username and password would be a better idea?

---

