---
title: "iptables config. Need feedback."
date: 2012-08-15
forum: Security
---

### Post by artheus on 2012-08-15
Hi,

I am setting up an iptables configuration for a server that is going to be running Apache and OpenVPN Publicly. I am aiming for a sollution where people are able to see some sites on the server by just browsing to it on port 80 (http) or 443 (https). But when the users connect to the OpenVPN, they should be able to get all internal services ( Full access to the server ). The internal services are such as ssh, internal dns, samba, http, https, etc.

 ( the internal dns will/shall not be exposed publicly, only the apache and openvpn servers are to be accessible publicly )

I have therefore come up with this iptables configuration to solve this. But I am quite new to iptables configurations. So I would like to see if any of you can give any input on this. Input like tips, if there are any risks by using my config, etc.

I am using the '-P OUTPUT ACCEPT' for the server to freely update software, update dns records etc. Might this rule pose as a threat to the security of my server?

The server is connected straight to the Internet without any HW-firewall in between.

This is the exact config script I am using:
```
#!/bin/bash

# Flush all existing rules
iptables -F
iptables -X

# Set default filter policy
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP

# Unlimited traffic for device lo
iptables -A INPUT -i lo -j ACCEPT

# Unlimited traffic for device tap0
iptables -A INPUT -i tap0 -j ACCEPT

# Special rules for device eth0

# OpenVPN
iptables -A INPUT -p udp -s 0/0 --dport 1194 -m state --state NEW,ESTABLISHED -j ACCEPT -i eth0

# HTTP
iptables -A INPUT -p TCP -s 0/0 --dport 80 -j ACCEPT -i eth0
iptables -A INPUT -p TCP -s 0/0 --sport 80 -j ACCEPT -i eth0

# HTTPS
iptables -A INPUT -p TCP -s 0/0 --dport 443 -j ACCEPT -i eth0
iptables -A INPUT -p TCP -s 0/0 --sport 443 -j ACCEPT -i eth0

# DNS
iptables -A INPUT -p UDP -s 0/0 --sport 53 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -p TCP -s 0/0 --sport 53 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT

```

Thanks for any feedback on this matter,
Artheus

---

