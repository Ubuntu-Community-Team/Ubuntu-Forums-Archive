---
title: "IP Tables - block all but specified users"
date: 2011-01-10
forum: Server Platforms
---

### Post by louise100 on 2011-01-10
Hi there,

Can someone tell me if there is something obviously wrong with this code?

I am trying to block all smtp access except for specified users....

[PHP]/sbin/iptables -A OUTPUT -d 127.0.0.1 -p tcp -m tcp --dport 25 -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp -m tcp --dport 25 -m owner --gid-owner mail -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp -m tcp --dport 25 -m owner --uid-owner root -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp -m tcp --dport 25 -m owner --uid-owner postfix -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp -m tcp --dport 25 -j REJECT --reject-with icmp-port-unreachable
[/PHP]This code was provided by my hosting company.  However, once the last line is added, mail is no longer sent...

Any help would be appreciated,

Thanks! :)

---

