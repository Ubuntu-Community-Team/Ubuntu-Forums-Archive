---
title: "Iptables for redirect ip traffic to new server with different ip"
date: 2012-08-28
forum: Server Platforms
---

### Post by farenheitcx on 2012-08-28
Today I able to migrate some of the game servers to another  server and needed some help to redirect the traffic from old ip to the  new one.
  SERVER1 1.1.1.1 ----- (internet ) -----> SERVER 2.2.2.2
  I asume to use iptables to perform this, for that used this rule on my centOS box in the server1.


```
/etc/sysctl.conf: net.ipv4.ip_forward = 1
```
    ```
iptables -t nat -A PREROUTING -p udp --dest 1.1.1.1 --dport 27015 -j DNAT --to-destination 2.2.2.2:27015 iptables -t nat -A POSTROUTING -j MASQUERADE iptables -t nat -A POSTROUTING -d 2.2.2.2 -p udp --dport 27015 -j SNAT --to 1.1.1.1
```   But the client cannot connect to the server from the old ip, the redirection don't started.

---

