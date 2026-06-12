---
title: "route trouble"
date: 2012-07-21
forum: Server Platforms
---

### Post by kdzida on 2012-07-21
I have a 2 networks:

192.168.1.0 - internal (I have full access to this network)
192.168.2.0 - external 

192.168.2.1 - gateway to internet (and dhcp server for external network)


My router is Ubuntu 12.4 LTS 64 bit with 2 network adapters:

eth1 - 192.168.1.1 mask 255.255.255.0 (internal network)
eth2 - 192.168.2.101 mask 255.255.255.0 (external network)

(no eth0)

route is 
```

Destination    Gateway        Genmask        Flags   Metric    Ref    Use       Iface
default        192.168.2.1    0.0.0.0          UG    100       0       0        eth2
192.168.1.0     *             255.255.255.0     U     0        0       0        eth1
192.168.2.0     *             255.255.255.0     U     0        0       0        eth2

``````

cat /proc/sys/net/ipv4/ip_forward
1

```The problem is that Linux/Windows clients on 192.168.1.0 (internal network) have no connection to external network. The computers  on 192.168.1.0 can ping router on 192.168.1.1 and even 192.168.2.101 (!) but not anything else on external network or internet.

route on (Ubuntu) clients on internal (192.168.1.0) is
```

Destination        Gateway         Genmask         Flags Metric Ref    Use    Iface
default            192.168.1.1     0.0.0.0            UG    0      0        0    eth0
link-local         *               255.255.0.0     U     1000   0        0    eth0
192.168.1.0        *               255.255.255.0   U     1      0        0    eth0

```What am I doing wrong?

---

### Post by SeijiSensei on 2012-07-21
I'll bet that the router at 192.168.2.1 has no static route configured for the 192.168.1.0/24 network.  You need to tell that router to route packets for 192.168.1.0/24 via the Ubuntu box at 192.168.2.101.  Without that route, the 2.1 router will send those packets out its default route, which I suspect is the Internet.

---

### Post by kdzida on 2012-07-21
But clients on internal net (192.168.1.0) can't ping computers on the internet too!

I don't mind if 192.168.1.0 clients will not be able to speak with 192.168.2.0 computers but I really need the internet connection (192.168.2.1).

---

### Post by koenn on 2012-07-21
> **kdzida said:**
> But clients on internal net (192.168.1.0) can't ping computers on the internet too!

I don't mind if 192.168.1.0 clients will not be able to speak with 192.168.2.0 computers but I really need the internet connection (192.168.2.1).

you're computers on 192.168.1.0 already have internet access, it's just that the replies from servers on the internet can't reach them, exactly for the reason Sensei explained. 

Those replies arrive at 192.168.2.1. How are they supposed to get to 192.168.1.0 ? And how would 192.168.2.1 know that ?

---

