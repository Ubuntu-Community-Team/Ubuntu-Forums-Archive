---
title: "[ASK] Ping to server with 2 IP Address"
date: 2016-12-27
forum: Server Platforms
---

### Post by Indra_ivan on 2016-12-27
Hi,

I just recently try to configure network routing in ubuntu and I have a question.

I have 2 Server and 1 PC here's the network configuration for each : 

Server 1 :
IP 1 : 172.16.1.206 (default)
IP 2 : 172.16.15.213

Server 2 :
IP : 172.16.15.212

PC : 
IP : 172.16.3.6

When i'm doing with fresh installation for server 1, 
- from my PC I can ping to 172.16.1.206, cannot ping to 172.16.15.213
- from server 2 I can ping to 172.16.15.213, cannot ping to 172.16.1.206

When I add static route for 172.16.15.213, from my PC I can ping both of IPs but still the same from Server 2.

Can someone help me ?
My aim is for Server 2 can ping both of IPs Server 1.

Best Regards,
Indra Ivan

---

### Post by wildmanne39 on 2016-12-27
*Thread moved to **Server Platforms**.*

---

### Post by volkswagner on 2016-12-29
Please provide a graphic of your network topology, include network/mask and ip, router(s), switch, etc.

Please provide route table for each machine.

For linux:
```
route
```


For windows:
```
route print
```

---

### Post by SeijiSensei on 2016-12-29
Are you using a "class-B" subnet with netmask 255.255.0.0, aka 172.16.0.0/16, or separate "class-C" networks, 172.16.1.0/24, 172.16.3.0/24, and 172.16.15.0/24?  In the latter case you'll need some machine to act as a router.

Make sure you have removed the hash mark ("#") from the line "net.ipv4.ip_forward" in /etc/sysctl.conf.  If you have not done so, remove the hash mark and reboot.  Any better?

---

