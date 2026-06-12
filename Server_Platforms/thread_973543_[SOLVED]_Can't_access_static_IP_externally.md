---
title: "[SOLVED] Can't access static IP externally"
date: 2008-11-06
forum: Server Platforms
---

### Post by Thirtysixway on 2008-11-06
I have the computers here in my home getting their IP from DHCP via my linksys router.  The addresses start at 192.168.1.100, so I set my ubuntu server to have a static IP address at 192.168.1.10 (as to be out of range of the dhcp addresses)

/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.10
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        post-up iptables-restore < /etc/iptables.up.rules

```

So I restarted networking, forwarded my ports (80 right now) on the router to point to 192.168.1.10 but the external IP address, as well as my dynamicdns url both do not load, but it loads inside the lan (typing [http://192.168.1.10](http://192.168.1.10) into the browser).


Is there something I'm missing?  I've gotten this to work before plenty of times when my server was using DHCP, it just doesn't want to work with a static ip... :confused:

---

### Post by gtdaqua on 2008-11-06
sorry. am trying to delete this post.

---

### Post by mindwarp on 2008-11-06
If it works on the local network, and not through your router's port forwarding, I would recommend checking your routers config again, power cycling the device, and check the firmware levels.

---

### Post by Thirtysixway on 2008-11-07
Hm.  Doesn't seem to be working.  I might just have to go back to using dhcp for the ip address, but that's not very reliable.

---

