---
title: "Ubu Server 10 connection problem"
date: 2016-06-20
forum: Server Platforms
---

### Post by givecake on 2016-06-20
Hi all.

The network was running fine yesterday, but today it's not doing anything productive. I don't know what the problem could be.
The network card is detected and shows up with lspci, and eth0 is up, but doesn't appear to be 'running'. 

ifconfig shows:

```

eth0     Link encap:Ethernet    HWaddr 00:10:18:2c:13:b7
           inet addr:10.4.56.3     Bcast:10.4.56.255    Mask:255.255.255.0
           UP BROADCAST MULTICAST   MTU:1500   Metric:1
           RX packets:0  errors:0  dropped:0  overruns:0  frame:0
           TX packets:0  errors:0  dropped:0  overruns:0  carrier:0
           collisions:0  txqueuelen:1000
           RX bytes:0 (0.0 B)   TX bytes:0 (0.0 B)
           Interrupt:16

```

route shows:

```

Destination     Gateway       Genmask                 Flags   Metric   Ref       Use   Iface
localnet          *                255.255.255.0          U        0         0             0    eth0
default           10.4.56.11    0.0.0.0                   UG       100      0            0     eth0

```

It can only ping itself, and not other networked computers nor internet sites. 
I tried 'sudo dhclient eth0' and after a while, it told me 'No DCHPOFFERS received'. The ethernet cable seems fine because the lights are on. 

Anyone know what all this could mean?

P.S. Sorry for the odd formatting. And I'll try a live-cd to make sure the card is working properly.

---

### Post by Bucky Ball on 2016-06-20
Does 'Ubu Server 10' mean Ubuntu Server 10.04 LTS? If so, it's no longer supported.

Doesn't help with your issue ... or does it? Just wanting to confirm and let you know.

---

### Post by givecake on 2016-06-20
Hi Bucky, yeah it means 10.04. I realise it's no longer supported, but the software it's running is not so easy (read: I don't know how) to set up on a newer version. I haven't tried the latest, but technically, this *should* be a small fix, right? I mean, afaik, nothing at all changed, yet something has changed.

---

### Post by TheFu on 2016-06-21
Maybe the machine has been hacked?  It is unsupported and the forum rules, as I understand them, don't allow unsupported systems.
[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)

Networking in linux changed since 10.04 - mainly the GUI tools and resolvconf package. Can you ping the router and the DHCP server? That is where I'd start.

---

