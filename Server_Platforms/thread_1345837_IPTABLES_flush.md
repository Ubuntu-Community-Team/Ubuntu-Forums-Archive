---
title: "IPTABLES flush"
date: 2009-12-04
forum: Server Platforms
---

### Post by wwoollff on 2009-12-04
Hi. I use a firewall script to generate all the rules for a LAN of about 50 computers, running on a Ubuntu Server machine( eth0-internet eth1-local). 
I would like to block all internet traffic from 00:00 to 07:00, but when I execute the script:
```

#!/bin/sh
iptables -F
iptables -t nat -F
iptables -X
iptables -t nat -X
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
#allow loopback
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
#allow lan traffic 
iptables -A INPUT -i eth1 -j ACCEPT
iptables -A OUTPUT -o eth1 -j ACCEPT
#allow ssh from outside
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -m state --state NEW -j ACCEPT
#drop everything else
iptables -A INPUT -j DROP
iptables -A OUTPUT -j DROP
iptables -A FORWARD -j DROP
```
all traffic drops, except for Yahoo Messenger. And probably all established connections,like torrents etc.
I have added the line ```
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j DROP
``` before ```
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j DROP

```, then all connection dropped, I couldn't connect through ssh to the server from a computer in the LAN, and yahoo messenger from another host crashed..

How can I drop all traffic, including active connections, and allow only LAN traffic, but without these weird crashes?

Thanks alot.

---

### Post by ayenack on 2009-12-04
Personally I wouldn't use iptables for this I'd use a cron.

```
sudo crontab -e
```

Then add this:-

```
0 0 * * * /usr/bin/sudo ifdown eth0

0 7 * * * /usr/bin/sudo ifup eth0
```

That's how I'd do it. Hope it helps.

---

### Post by wwoollff on 2009-12-04
Simple,but effective. Thank you for your solution.

---

### Post by wwoollff on 2009-12-12
back with an edit: after I do sudo ifdown eth0, I cannot ping any exterior server, the http traffic stopped in the LAN, but yahoo messenger is still working! although eth0 is down!...I cannot believe this...

---

