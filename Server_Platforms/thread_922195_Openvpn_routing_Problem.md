---
title: "Openvpn routing Problem"
date: 2008-09-17
forum: Server Platforms
---

### Post by iLLiCiTgr on 2008-09-17
Hello guys. I'm having trouble routing openvpn on my server.
I'm currently having several ips on the server on 2 subnets
85.x.x.224/27 from which i own .254
and
78.xx.xx.88/29 from which 89-95 are usable for me.

I have used a subnet of 10.8.1.0 for my openvpn.
I've successfully routed the 78.x subnet so the traffic goes through vpn.
But when ever i am trying to route the 85.x ip, all of my computers traffic stops.

I've tried this on windows clients, on my ubuntu client and still no luck

This is my clients routing

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.1.5        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
78.xx.xx.88     10.8.1.5        255.255.255.248 UG    0      0        0 tun0
192.168.192.0   0.0.0.0         255.255.255.0   U     0      0        0 br0
10.8.1.0        10.8.1.5        255.255.255.0   UG    0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.192.1   0.0.0.0         UG    100    0        0 br0

While on my server the routing goes as this

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.1.2        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
78.xx.xx.88     0.0.0.0         255.255.255.248 U     0      0        0 eth0
85.xx.xx.224   0.0.0.0         255.255.255.224 U     0      0        0 eth0
10.8.1.0        10.8.1.2        255.255.255.0   UG    0      0        0 tun0
0.0.0.0         85.xx.xx.225   0.0.0.0         UG    100    0        0 eth0
0.0.0.0         85.xx.xx.225   0.0.0.0         UG    100    0        0 eth0
0.0.0.0         85.xx.xx.225   0.0.0.0         UG    100    0        0 eth0
0.0.0.0         85.xx.xx.225   0.0.0.0         UG    100    0        0 eth0
0.0.0.0         85.xx.xx.225   0.0.0.0         UG    100    0        0 eth0
0.0.0.0         85.xx.xx.225   0.0.0.0         UG    100    0        0 eth0

I have tried manually adding route to my ubuntu client

route add -host 85.xx.xx.254 gw 10.8.1.5 netmask 255.255.255.255 metric 0
route add -net 85.xx.xx.224 gw 10.8.1.5 netmask 255.255.255.224 metric 0

and yet, no luck.

I've even tried pushing the route 85.xx.xx.254 255.255.255.255 from the openvpn configuration and again, nothing.

Can anyone help me?

---

### Post by iLLiCiTgr on 2008-09-19
Anyone? Should i repost this on the network subforum?
I really need help as soon as possible...:(

---

### Post by iLLiCiTgr on 2008-09-21
Never mind. I will repost this on the network forum

---

