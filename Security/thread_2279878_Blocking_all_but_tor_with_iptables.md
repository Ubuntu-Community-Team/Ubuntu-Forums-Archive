---
title: "Blocking all but tor with iptables"
date: 2015-05-26
forum: Security
---

### Post by jim50 on 2015-05-26
Hi all,

I know this has been asked a few times, and I've been googling around but I keep getting stuck.

I want to block all trafic from my system that does not use tor. It's a virtualbox VM running on an ubuntu host. 

so far I've tried ```

sudo iptables -P INPUT DROP
sudo iptables -A INPUT -s 127.0.0.1 -d 127.0.0.1 -j ACCEPT
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -P OUTPUT DROP
sudo iptables -A OUTPUT -s 127.0.0.1 -d 127.0.0.1 -j ACCEPT
sudo iptables -A OUTPUT -m owner --uid-owner debian-tor -j ACCEPT
```

and ```

iptables -F OUTPUT
# iptables -A OUTPUT -j ACCEPT -m owner --uid-owner debian-tor
# iptables -A OUTPUT -j ACCEPT -o lo
# iptables -A OUTPUT -j ACCEPT -p udp --dport 123
# iptables -P OUTPUT DROP
# iptables -L -v 
```
from the tor site, but both seem to just block all traffic?

betweeen each I've reset my iptables back to clear with ```

 ip6tables --policy INPUT   ACCEPT
 ip6tables --policy OUTPUT  ACCEPT
 ip6tables --policy FORWARD ACCEPT
 ip6tables -Z
 ip6tables -F
 ip6tables -X
 iptables --policy INPUT   ACCEPT
 iptables --policy OUTPUT  ACCEPT
 iptables --policy FORWARD ACCEPT
 iptables -Z
 iptables -F
 iptables -X
```

Thanks in advance ladies and gents!

---

### Post by fugu2 on 2015-05-26
You should take a look at the TAILS distro, then run ```
$ sudo iptables-save
``` to get an idea of how this can be done

---

