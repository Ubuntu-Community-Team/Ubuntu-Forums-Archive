---
title: "I cannot connect to the Internet or Ping LAN"
date: 2017-10-22
forum: Server Platforms
---

### Post by jamesnash16 on 2017-10-22
Hello, I have been ha ING some issues with Ubuntu server, I can ping 127.0.0.1 and my own IP address but not any other LAN pc or my router, the Ubuntu server doesn't show up in the router either, any suggestions? Thanks

---

### Post by wildmanne39 on 2017-10-22
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by darkod on 2017-10-22
Your networking setup doesn't seem correct. Post the output of the following:
```
cat /etc/network/interfaces
ifconfig
route -n
cat /etc/resolv.conf
```

---

### Post by LHammonds on 2017-10-23
[SIZE=4]Total guesswork scenario #1:[/SIZE]

Let's assume the following IP addresses:

Server IP: 192.168.0.2
Router IP: 192.168.0.1

In this scenario, either your network cable is not plugged in, or plugged into the wrong NIC if you have multiple or you failed to reference 192.168.0.1 as your gateway.

Example /etc/network/interfaces for the above scenario:

```

iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1
network 192.168.0.0
broadcast 192.168.0.255
dns-nameservers 192.168.0.1 8.8.8.8

```

[SIZE=4]Total guesswork scenario #2:[/SIZE]

Let's assume the following IP addresses:

Server IP: 192.168.1.1
Router IP: 192.168.0.1

In  this scenario, your server and your router are on two different network segments.  If your router is not configured for bridging those networks, it simply will not work.  Also, many machine's default firewall behavior is to block all communication from devices in different local area networks (e.g. anything not on their subnet).

Solution would be to put the server on the same LAN segment.  e.g. 192.168.0.2

LHammonds

---

