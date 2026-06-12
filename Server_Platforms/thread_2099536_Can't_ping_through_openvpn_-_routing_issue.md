---
title: "Can't ping through openvpn - routing issue?"
date: 2012-12-29
forum: Server Platforms
---

### Post by DarkGreen16 on 2012-12-29
I'm trying to setup certain applications to go through openvpn and then the rest of the items to go through my regular ISP.

So far I have the vpn configured and it connects successfully but it only allows me to ping out using the ping -I tun0 when I have

```
redirect-gateway
```

enabled in my vpn configuration.

If I take that option out I can still connect but any attempts to ping out across the interface receive no response - I assume this is because the response isn't being sent to the correct interface.

I've done quite a bit of googling but since everyones setup seems to be different its been difficult to match to mine.

My setup

```
eth0      Link encap:Ethernet
          inet addr:192.168.44.101  Bcast:192.168.44.255  Mask:255.255.255.0
          inet6 addr: fe80::215:5dff:fe50:ac0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:94148456 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121186740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:43935235906 (43.9 GB)  TX bytes:150304727195 (150.3 GB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28125004 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28125004 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:270169363923 (270.1 GB)  TX bytes:270169363923 (270.1 GB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.1.0.6  P-t-P:10.1.0.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:756 (756.0 B)  TX bytes:756 (756.0 B)

```


routing

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.44.1    0.0.0.0         UG    0      0        0 eth0
10.1.0.1        10.1.0.5        255.255.255.255 UGH   0      0        0 tun0
10.1.0.5        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
192.168.44.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0

```

Any assistance would be appreciated.

---

### Post by spynappels on 2012-12-30
Ok, a couple of things first, can you ping your VPN server on 10.1.0.1?

Also, was the routing table printed with the VPN active? I suspect it was but the default route is still set to the eth0 interface.

What traffic are you trying to send through the VPN?

---

### Post by DarkGreen16 on 2012-12-30
Hey spynappels - thanks for the reply


Yes, I can ping the server at 10.1.0.1 - when I connect to my provider this may also be 10.2.0.1 at times so I need to somehow accommodate for that in my setup as well.

The routing table was printed when the VPN was active.


I'm trying to just send torrent traffic through it for now. I successfully have qbittorrent bound to that interface but since I can't do any communication through it at all, it doesn't do me any good.


I was originally trying to do this with transmission but it seemed to lack the ability to bind to a specific interface.

---

### Post by spynappels on 2012-12-30
Ok, that makes sense. I think the problem is actually on the OpenVPN server you are connecting to, in that it either doesn't know what to do with the packets it receives from the client, or with the response. It's been a while since I've done anything with OpenVPN but I'll try and remember the stuff I used to do to get mine working.

In the meantime, can you check that ipv4_forwarding is enabled on the OpenVPN server?

On the IP conflict issue, you could run a second OpenVPN daemon on another port using an ip subnet like 10.250.x.x to connect to in the case of a conflict in the lower range. Gives you a backup system as it were.

---

### Post by DarkGreen16 on 2013-01-03
sorry for the late reply - I decided to just avoid the headache and go with a proxy service instead of a vpn service.

thanks for the efforts

---

