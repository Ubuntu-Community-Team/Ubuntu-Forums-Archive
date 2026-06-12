---
title: "Port 80 -&gt; virbr0 possible?"
date: 2013-06-05
forum: Server Platforms
---

### Post by shimie on 2013-06-05
Hi,
i moved my Webserver into a VM virtualized with virsh/qemu, but i have only one IP-Address also i should forward port 80 from my Internetip to 192.168.122.134.

I tryed iptables:

```
/sbin/iptables -t nat -A POSTROUTING -o vnet0 -s 192.168.122.134 -j SNAT --to 192.168.178.29
/sbin/iptables -t nat -A PREROUTING -d 192.168.178.29 -p tcp --dport 80 -j DNAT --to 192.168.122.134:80
```

if:
```
virbr0    Link encap:Ethernet  Hardware Adresse fe:54:00:49:93:3c            inet Adresse:192.168.122.1  Bcast:192.168.122.255  Maske:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:669078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:780830 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX-Bytes:40428499 (40.4 MB)  TX-Bytes:1120365670 (1.1 GB)
```

But i dosent work, has anybody a idea what could help? rined isn't a option because i need the real IPs.

---

### Post by sandyd on 2013-06-05
> **shimie said:**
> Hi,
i moved my Webserver into a VM virtualized with virsh/qemu, but i have only one IP-Address also i should forward port 80 from my Internetip to 192.168.122.134.

I tryed iptables:

```
/sbin/iptables -t nat -A POSTROUTING -o vnet0 -s 192.168.122.134 -j SNAT --to 192.168.178.29
/sbin/iptables -t nat -A PREROUTING -d 192.168.178.29 -p tcp --dport 80 -j DNAT --to 192.168.122.134:80
```

if:
```
virbr0    Link encap:Ethernet  Hardware Adresse fe:54:00:49:93:3c            inet Adresse:192.168.122.1  Bcast:192.168.122.255  Maske:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:669078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:780830 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX-Bytes:40428499 (40.4 MB)  TX-Bytes:1120365670 (1.1 GB)
```

But i dosent work, has anybody a idea what could help? rined isn't a option because i need the real IPs.

Your ifconfig shows your IP Address is 192.168.122.1, but you are routing to 192.168.122.134?

Also, make sure there are no firewalls in between.

---

### Post by shimie on 2013-06-05
> **sandyd said:**
> Your ifconfig shows your IP Address is 192.168.122.1, but you are routing to 192.168.122.134?



Yes because 192.168.122.1 is only the gateway, 192.168.122.134 is the vm ip.

---

