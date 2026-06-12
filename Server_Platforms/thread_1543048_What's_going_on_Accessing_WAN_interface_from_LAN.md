---
title: "What's going on: Accessing WAN interface from LAN"
date: 2010-07-31
forum: Server Platforms
---

### Post by Tukanfan on 2010-07-31
Hi! :D
I'd like to know what's going on here:
I have a router (Fit-PC2i) running Ubuntu Server 10.04 LTS. It has two ethernet interfaces - a WAN (internet) one and a LAN one. The router is also a NAT device, hence my LAN is a 192.168.0.0/24.

I have a FQDN too but no DNS servers myself. Therefore, I'm using a external DNS Service called gratisdns.dk which is authoritative for my FQDN. Because my LAN is a so-called "private" LAN, the only A record in my FQDN points to the WAN interface of my router.

Now if I, for instance, try to SSH into my router from the LAN using it's domain name, SSH resolves it to the IP address of the routers WAN interface and lets me log in.

Doing a tracepath from the LAN gives me this:
```

 1:  192.168.0.202 (192.168.0.202)     0.049ms pmtu 1500
 1:  1.2.3.4 (1.2.3.4)                 0.866ms reached
 1:  1.2.3.4 (1.2.3.4)                 0.841ms reached
     Resume: pmtu 1500 hops 1 back 64 

```
assuming 1.2.3.4 is the IP-address of the routers WAN interface.

A traceroute gives me this:
```

 1  95.154.44.108 (95.154.44.108)  0.189 ms  0.152 ms  0.142 ms

```

So, I would like to know what's happening inside the router (generally seen) when I send a packet from the LAN to it's WAN interface. I would also be pleased to know whether or not there should be taken any security precautions against it.

Best Regards

---

