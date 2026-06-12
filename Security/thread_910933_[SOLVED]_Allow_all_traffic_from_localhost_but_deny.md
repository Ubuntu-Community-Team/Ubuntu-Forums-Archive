---
title: "[SOLVED] Allow all traffic from localhost but deny incoming from outside using iptabl"
date: 2008-09-05
forum: Security
---

### Post by kalesh7 on 2008-09-05
ok I spent about half a day getting an answer to this so I thought to put it here incase anyone else needs it? Useful for programmers using their pc as a development server.
I have apache, mysql, and a bunch of other stuff running on my pc and I wanted to be able to access them from localhost (my pc) but not allow any access from anywhere else while allowing any and all outbound traffic.

This is what worked in the end

```

iptables -F
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
iptables -A OUTPUT -o ppp0 -j ACCEPT
iptables -A INPUT -i ppp0 -m state --state ESTABLISHED,RELATED -j ACCEPT

```
a short explanation of what the commands do

the first one removes all rules from iptables(you may or maynot want to do this)

the next three drop all connections from to anywhere

the next two
```
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
```
accept all traffic coming from your computer to your computer

the next one 
```
iptables -A OUTPUT -o ppp0 -j ACCEPT
```
accepts all outbound traffic from your computer

and the last one accepts inbound traffic to your computer coming in response to a request from your computer(not having this will prevent you from using the internet)

Hope it can help someone sometime

---

### Post by Titan8990 on 2008-09-05
People should note that this is for use with a modem. Most users will want to substitute eth0 for ppp0.


Also, you could have set a default policy for the outbound chain instead of using a specific rule.

---

