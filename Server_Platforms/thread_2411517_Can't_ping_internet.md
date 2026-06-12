---
title: "Can't ping internet"
date: 2019-01-31
forum: Server Platforms
---

### Post by orangepathogen on 2019-01-31
I started having a problem in ubuntu server recently where I can't ping anything outside my local network. I'm not exactly sure what made it stop working, maybe some recent package updates. I'm not sure how to start troubleshooting this. How do I get started?

---

### Post by TheFu on 2019-01-31
Can you ping the router by IP?

What is the route?

Can you ping 8.8.8.8?  It could just be a DNS issue.

---

### Post by orangepathogen on 2019-01-31
Can't ping 8.8.8.8.
```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 enp0s3
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
172.19.0.0      0.0.0.0         255.255.0.0     U     0      0        0 br-c93769cdf9df
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 enp0s3

```

---

### Post by TheFu on 2019-01-31
Which ubuntu version? I can't help with 18.04 or later, sorry.  Netplan scares me.

Have you tried removing the bridge and docker?

Can you ping the router by IP?

What is the IP address of the system you want networking from?

---

### Post by orangepathogen on 2019-01-31
I'm using 18.04.01. I'm not sure what you mean by removing the bridge, but I haven't tried removing docker. I need docker to work because it's the whole point of running the server for me. I have two routers, but I can't ping either. Networking should come from 192.168.1.1 but I have another router in between to act as a wireless bridge.

I have a working Ubuntu desktop virtual machine. Is there a way to copy that configuration?

---

### Post by TheFu on 2019-01-31
I can only advise to simplify and test until you determine the root issue.  I would first simplify the networking, assuming you believe the NIC and drivers for it are all fine.  Until you can ping the local router, nothing else should be expected to work.

You might need to disable the docker parts during troubleshooting.

So I would physically connect, via wire, the system and the working router.  Try pinging it by IP.  If that doesn't work and the networking is all on the same LAN, simple subnetting, then the next thing to check is that the driver and the NIC match and work.  **sudo lshw -C networking **can help.

---

### Post by orangepathogen on 2019-01-31
I'm not sure what changed but it started working all of a sudden. I let it alone and came back and saw that networking was fine.

---

### Post by wildmanne39 on 2019-01-31
*Thread moved to **Server Platforms a more appropriate sub-forum**.*

---

### Post by TheFu on 2019-01-31
> **orangepathogen said:**
> I'm not sure what changed but it started working all of a sudden. I let it alone and came back and saw that networking was fine.

That isn't good. It means you have an unsolved issue that will likely reappear.  Something is flaky in the setup.

---

