---
title: "Vpn (pptp) route to internet?"
date: 2011-01-11
forum: Server Platforms
---

### Post by Dr_Deadmeat on 2011-01-11
Hi everybody.

I have a strange problem when I am using vpn to connect to my server remotely. When I try to browse some webpages while connected to vpn, my windows boxes can only load googles homepage (tracert shows me a proper route), but when I am on my linux boxes, I can browse the internet when I am connected to the vpn. Do anyone know what the problem might be? The config I have done for routing is enable net.ipv4.ip_forward=1 in /etc/sysctl and I have put this command in /etc/rc.local
```
 iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
```

Thats the only routing configuration I have done. It is worth mentioning that I can connect to my server and use remote desktop which is the reason for me to have vpn in the first place... Any help would be appreciated =)

---

