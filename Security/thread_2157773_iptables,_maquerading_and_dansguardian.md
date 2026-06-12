---
title: "iptables, maquerading and dansguardian"
date: 2013-06-26
forum: Security
---

### Post by cschambers2101 on 2013-06-26
Hi,

I want to set up a box for a college network that will port forward from eth1 - 172.16.x.x (green) to eth0 192.168.x.x (red) while passing all web traffic (http, https) through dans guardian (installed on the same box).

The set up side is fine. What I need help with is the iptables rules to configure this. When I set this up, everything forwards but dans doesn't work.

-A OUTPUT -p tcp -m owner ! --uid-owner 13 -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A POSTROUTING -s 172.16.0.0/24 -o eth0 -j MASQUERADE

Any ideas?

---

### Post by Kujua on 2013-06-27
> -A OUTPUT -p tcp -m owner ! --uid-owner 13 -m tcp --dport 80 -j REDIRECT --to-ports 8080
Are you trying to redirect only traffic from your box? Because OUTPUT chain is used only for locally generated traffic. So the above rule will not be applied for traffic forwarded from 172.16.x.x to 192.168.x.x.
If you want to redirect forwarded traffic the rule should be added to PREROUTING.

---

### Post by alf4 on 2013-09-17
My question was related to the closed thread [http://ubuntuforums.org/showthread.php?t=1415724](http://ubuntuforums.org/showthread.php?t=1415724)

the iptables entry:
[FONT=Courier New]iptables -t nat -A PREROUTING -i br0 -p tcp --dport 80 -j REDIRECT --to-port 8080[/FONT]
[FONT=Verdana]works fine but it stops some php POST and GET for a time based hotspot session initialisation. 
I have no idea what kind of handshaking takes place between the local gateway and the remote one to start a new session but the firewall stops it. 
I added exceptions on [/FONT]dans guardian lists that now match as seen in access.log but it does not go any further and the walled garden is waiting for some information from external gateway.
Any idea where I can start from?
Thanks

---

