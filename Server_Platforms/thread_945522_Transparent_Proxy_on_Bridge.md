---
title: "Transparent Proxy on Bridge"
date: 2008-10-12
forum: Server Platforms
---

### Post by radonk on 2008-10-12
Hi All,

i know there are a lot of tutorials how to setup a transparent proxy but i could not really find it how to do it on a bridge.

My setup:

Net 192.168.20.0/24
GW  192.168.20.1

The Linux box:

eth0 192.168.20.252	SSH Only

eth1 192.168.20.253
eth2 192.168.20.254

bridge01
     eth1
     eth2


The bridge is working and the squid server is running
fine on port 3128. If i setup the proxy server in the
browser manual everything is working.

My problem is now how do i get squid to capture and cache
the traffic which is going over the bridge on port 80????


I hope you can help me.

If you need any more information please let me know.

Cheers
Karsten

---

