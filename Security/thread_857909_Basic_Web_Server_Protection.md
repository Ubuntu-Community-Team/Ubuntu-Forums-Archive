---
title: "Basic Web Server Protection?"
date: 2008-07-13
forum: Security
---

### Post by EMCGFX on 2008-07-13
Hello, can some one please point me in the right direction with iptables rules? What am I missing here, or what did I due wrong. Because when I apply this rules, I can access the server by ip but not by domain name. Btw, I would rather have OUTPUT chain on DROP instead of ACCEPT, but when I due that I can't access my server at all.
Thanks for any help ;)

Here is my rules:
```

#!/bin/bash

iptables -F
iptables -X

iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

## Allow ICMP Pings
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -i eth0 -j ACCEPT

## SYN Protection
iptables -A INPUT -p tcp --syn -m limit --limit 5/s -i eth0 -j ACCEPT

## Allow DNS
iptables -A INPUT -p udp --sport 53 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -p tcp --sport 53 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p udp --sport 1024:65535 --dport 53 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --sport 1024:65535 --dport 53 -m state --state NEW,ESTABLISHED -j ACCEPT

## Allow SSH
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT
## Limit Access to SSH later.

## Allow HTTP
iptables -A INPUT -p tcp -m tcp --sport 80 -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --dport 80 -j ACCEPT

## Allow HTTPS
iptables -A INPUT -p tcp -m tcp --sport 443 -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --dport 443 -j ACCEPT

```

---

