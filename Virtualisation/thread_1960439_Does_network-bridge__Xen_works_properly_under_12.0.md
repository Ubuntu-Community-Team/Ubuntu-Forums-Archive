---
title: "Does network-bridge / Xen works properly under 12.04 beta?"
date: 2012-04-17
forum: Virtualisation
---

### Post by Enolas on 2012-04-17
Hello,

I just installed the last beta of Ubuntu server ( 12.04 ) with Xen. 
When I'm trying to enable (network-script network-bridge) in /etc/xen/xend-config.sxp it breaks the network configuration of the server.
I thought it would work without creating the bridge myself?

Thank you,

---

### Post by inquirewue on 2012-04-29
I am running the release version of 12.04 and I seem to have the same problem in that no matter what config values I change or scripts that I run (scripts in /etc/xen/scripts/) seems to get a bridge configured at all. 

My /etc/xen/xend-congif.sxp file's networking lines:
```
(network-script network-bridge)
(vif-script vif-bridge)
```

Excerpt from my ifconfig output (MACs and IPs changed):
```
eth0      Link encap:Ethernet  HWaddr 00:ff:ff:ff:ff:ff
          inet addr:1.1.1.225  Bcast:1.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::333:90ff:ffff:3aff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Memory:fbce0000-fbd00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1

virbr0    Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
```

I've read many tutorials and manpages and nothing helps. It looks like I'll have to figure this out myself... I'll write a proper bash script or something and post my results here. **SIGH**

---

