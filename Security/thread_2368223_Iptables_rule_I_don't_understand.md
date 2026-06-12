---
title: "Iptables rule I don't understand"
date: 2017-08-08
forum: Security
---

### Post by ty89 on 2017-08-08
Hi guys.

I am trying to build my iptables fw to function as a gw router and came across this rule:


# Don't forward from the outside to the inside.
iptables -A FORWARD -i eth1 -o eth1 -j REJECT

But I don't understand why it should be -o eth1 and not -o eth0 if eth0 is inside lan and eth1 is external network. Is this correct?

---

### Post by mwoosley on 2017-08-08
ty89, I know this won't answer your question directly, but I found this article regarding changing the interface id. [B][http://tinyurl.com/j75sk4g](http://tinyurl.com/j75sk4g)
[/B]

I am a newbie and am also trying to study up on the iptables routine and find a good fit for my machine/server. 

Good luck and I hope you find a great solution :D

---

### Post by SeijiSensei on 2017-08-08
> **ty89 said:**
> 
# Don't forward from the outside to the inside.
iptables -A FORWARD -i eth1 -o eth1 -j REJECT


It's clearly a typo.  The rule should read
```
iptables -A FORWARD -i eth0 -o eth1 -j REJECT
```
assuming eth0 points to the outside network, and eth1 points to the local network.  Otherwise you'd obviously use the reverse.

I'll note that this rule is usually unnecessary on most modern distributions since packet forwarding is disabled by default in /etc/sysctl.conf as it is in Ubuntu.  If you do want to forward some traffic in either direction, you'll need to enable packet forwarding by changing
```
net.ipv4.ip_forward=1
```
in sysctl.conf and writing the appropriate iptables rules.

---

### Post by ty89 on 2017-08-08
That's what I thought. Thanks. 

mwoosley, I'll check that link out. Thanks. Good luck to you too :p

---

