---
title: "Domain of LAN"
date: 2011-03-03
forum: Server Platforms
---

### Post by geohei on 2011-03-03
Hi.

When I install Ubuntu 10.04 server, the following appears in /etc/resolv.conf:

```
root@vm:~# cat /etc/resolv.conf
nameserver 192.168.1.1
domain fritz.box
search fritz.box
```
My router is indeed a Fritz!Box.

When mechanism (broadcast?) is involved so that Ubuntu knows that my router is a Fritz!Box?

I believe the router send this information to the installation process of Ubuntu during install.

Can I change "fritz.box" in /etc/resolv.conf safely without confusing Ubuntu or the network?

Can I change this router behavior inside the router configuration (the web interface doesn't offer something like this).

Thanks,

---

### Post by geohei on 2011-03-05
That's what I found out so far ...

The domain name is issued by the Fritz!Box.

It cannot be changed using regular (official) firmware.

The mechanism used by the Ubuntu server installation software is DHCP.

Regards,

---

### Post by Demented ZA on 2011-03-05
I see this often when I'm setting up servers. When installing Ubuntu, it autoconfigures the network interfaces. If you have it connected to a router, it wil, via DHCP, get this information from the router.

It can be changed, but you will have to write protect it to prevent it from being changed back again by DHCP, or you can disable DHCP for that interface and use static ips instead.

Before you go that route though, a little more info on what you are trying to do would be nice;

[LIST]
[*]are you trying to set up ubuntu server or desktop?
[*]are you running one or two interfaces?
[*]planning a firewall system?
[/LIST]

---

