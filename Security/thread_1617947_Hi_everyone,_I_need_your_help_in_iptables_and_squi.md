---
title: "Hi everyone, I need your help in iptables and squid proxy"
date: 2010-11-10
forum: Security
---

### Post by lovesunset21 on 2010-11-10
hi everyone, i am totally new in Linux and iptables. I need to set up an ip table and a transparent squid proxy as followed:

I have 3 machine:


Machine 1 works as a squid proxy. It has 2 interface eth1 and eth2.

eth1: 192.168.99.2 (Connect to eth1 of machine 2)
eth2: 192.168.98.2 (Connect to eth1 of machine 3)

machine 2 works as a webserver

eth1: 192.168.99.4


machine 3 works as a web client.

eth1: 192.168.98.4


my responsibility is to send all tcp traffic from machine 3 at port 80 to my squid proxy.

In order to fulfill the tasks, I have edited the squid.conf as followed:

```
http_access allow localnet
http_access allow localhost

```


and in machine 1, I tried 2 ip tables command:

```
iptables -t nat -A PREROUTING -i eth2 -p tcp --dport 80 -j DNAT --to 192.168.99.2:80
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 80
```

I don't know if it is right or wrong. Please give me a suggestion. Thank you so much. I need your help.

---

