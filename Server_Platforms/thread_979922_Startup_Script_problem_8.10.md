---
title: "Startup Script problem 8.10"
date: 2008-11-12
forum: Server Platforms
---

### Post by eighto2 on 2008-11-12
My current set up consists of 2 load balancers that I've set up using pen, and heartbeat for HA

I used sudo update-rc.d pen defaults
I've made a startup script using that does the following command:

```
pen -l /logs/pen/pen80.log -p /logs/pen/pen80.pid -H 192.168.0.29:80 192.168.0.30:80 192.168.0.32:80
```

The first IP is the main loadbalancer, and the other 2 are the web servers, this set up works perfectly on the main lb. The problem is now that hearbeat is installed, on the 2nd LB this script no longer starts up any more.
If I log in and start it manually it works perfectly and HA is achieved...
In the 2nd machine if I do ifconfig -a it reads as follows:
```
eth2      Link encap:Ethernet  HWaddr 00:0c:29:28:e6:fc
          inet addr:192.168.0.28  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe28:e6fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2195 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3687 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:318927 (311.4 KB)  TX bytes:727392 (710.3 KB)
          Interrupt:17 Base address:0x1400

eth2:0    Link encap:Ethernet  HWaddr 00:0c:29:28:e6:fc
          inet addr:192.168.0.29  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x1400



```

So what I'm assuming by the eth2:0 that this iface is being created by heartbeat, my question is how can i specifically make my script run after heartbeat is done, or atleast make it the last script to start?

---

