---
title: "routing problem?"
date: 2006-04-14
forum: Server Platforms
---

### Post by wins on 2006-04-14
I just setup my Linux server using Dapper. The server serves both as apache web server and network gateway for internal home network through masquerade. eth0 connects to the net through ISP DHCP server, while eth1 connects with internal network 192.168.18.X. The Dapper server being 192.168.18.1 for eth1.

I have also setup some IP restrictions to the apache server so that it will only serve internal network plus few other static IP outside. 

The above setup is fine for other machines to access the web server, except the Dapper server itself. If I access my web server from the Dapper itself, what Apache sees is always from the public IP of eth0, instead of the internal IP 192.168.18.1. Even I directly type [http://192.168.18.1](http://192.168.18.1) still turns out being accessed from public IP in Apache access log.

This makes me impossible to make Apache to allow web access from its own, because the public IP address is dynamic.

The route command will give:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
210.XX.YY.0   *               255.255.255.128 U     0      0        0 eth0
localnet        *               255.255.255.0   U     0      0        0 eth1
default         210.XX.YY.1   0.0.0.0         UG    0      0        0 eth0

Any idea would be highly appreciated. Thanks!

---

