---
title: "restart networking doesn't run interface commands"
date: 2012-12-07
forum: Server Platforms
---

### Post by STARDOUSER on 2012-12-07
I have a number of secondary IPs configured using the up parameter in /etc/network/interfaces. I noticed that if I just do "restart networking", those secondary IPs are not added. However, if I restart the system, the commands are run and the IPs are all assigned to the interface as expected.

Here's an example interfaces file (my real IPs are sanitized):
```
iface eth0 inet static
        address x.x.57.145
        netmask 255.255.255.192
        broadcast x.x.57.191
        gateway x.x.57.129
        dns-nameservers 8.8.8.8
        up   ip addr add x.x.57.97/30 dev eth0 label eth0:0
        down ip addr del x.x.57.97/30 dev eth0 label eth0:0

```

What do I do so that up commands are run and my changes take immediate effect, aside from rebooting?  The machine I'm working with is running Ubuntu 12.10 server x64.

---

