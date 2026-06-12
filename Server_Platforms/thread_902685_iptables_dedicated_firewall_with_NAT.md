---
title: "iptables dedicated firewall with NAT"
date: 2008-08-27
forum: Server Platforms
---

### Post by Naatan on 2008-08-27
Hi, I am setting up a firewall with NAT that basically has 2 pc's behind it,
they have to be able to connect to the internet with certain restrictions and "the internet" should be able to SSH to them, however I can not connect to them using the ports that I'm forwarding on the firewall.. please check my config 

```
*filter
:FORWARD DROP [0:0]
:INPUT DROP [0:0]
:OUTPUT ACCEPT [0:0]
:loga - [0:0]

# FORWARD
-A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -i eth4 -j ACCEPT
-A FORWARD -p tcp --dport 22 -o eth4 -d 172.128.5.10 -m conntrack --ctstate RELATED -m state --state NEW --syn -j ACCEPT
-A FORWARD -p tcp --dport 22 -o eth4 -d 172.128.5.11 -m conntrack --ctstate RELATED -m state --state NEW --syn -j ACCEPT

# INPUT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -p tcp -m state --state NEW --dport 22 -i eth5 -j ACCEPT

COMMIT

*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]

# PREROUTING
-A PREROUTING -i eth5 -p tcp --dport 2210 -j DNAT --to-destination 172.128.5.10:22
-A PREROUTING -i eth5 -p tcp --dport 2211 -j DNAT --to-destination 172.128.5.11:22

# POSTROUTING
-A POSTROUTING -o eth5 -j MASQUERADE

COMMIT
```

I am testing from inside my network, but it is on another range than the computers behind the firewall
I am on range 192.168, the computers behind the firewall on 172.128.. the firewall itself has 2 NIC's

If anyone can shed some light I would greatly appreciate it

---

### Post by de0xyrib0se on 2008-08-27
> **Naatan said:**
> Hi, I am setting up a firewall with NAT that basically has 2 pc's behind it,
they have to be able to connect to the internet with certain restrictions and "the internet" should be able to SSH to them, however I can not connect to them using the ports that I'm forwarding on the firewall.. please check my config 

```
*filter
:FORWARD DROP [0:0]
:INPUT DROP [0:0]
:OUTPUT ACCEPT [0:0]
:loga - [0:0]

# FORWARD
-A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -i eth4 -j ACCEPT
-A FORWARD -p tcp --dport 22 -o eth4 -d 172.128.5.10 -m conntrack --ctstate RELATED -m state --state NEW --syn -j ACCEPT
-A FORWARD -p tcp --dport 22 -o eth4 -d 172.128.5.11 -m conntrack --ctstate RELATED -m state --state NEW --syn -j ACCEPT

# INPUT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -p tcp -m state --state NEW --dport 22 -i eth5 -j ACCEPT

COMMIT

*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]

# PREROUTING
-A PREROUTING -i eth5 -p tcp --dport 2210 -j DNAT --to-destination 172.128.5.10:22
-A PREROUTING -i eth5 -p tcp --dport 2211 -j DNAT --to-destination 172.128.5.11:22

# POSTROUTING
-A POSTROUTING -o eth5 -j MASQUERADE

COMMIT
```

I am testing from inside my network, but it is on another range than the computers behind the firewall
I am on range 192.168, the computers behind the firewall on 172.128.. the firewall itself has 2 NIC's

If anyone can shed some light I would greatly appreciate it

Use this as your forwarding rules:

iptables -I FORWARD -p tcp -d 172.128.5.10 --dport 22 -j ACCEPT
iptables -I FORWARD -p tcp -d 172.128.5.11 --dport 22 -j ACCEPT

Also your PREROUTING rules need to be:

iptables -A PREROUTING -t nat -i eth5 -p tcp --dport 2210 -j DNAT --to 172.128.5.10:22
iptables -A PREROUTING -t nat -i eth5 -p tcp --dport 2211 -j DNAT --to 172.128.5.11:22

---

