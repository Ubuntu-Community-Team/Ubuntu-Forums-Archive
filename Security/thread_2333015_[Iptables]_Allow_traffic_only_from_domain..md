---
title: "[Iptables] Allow traffic only from domain."
date: 2016-08-06
forum: Security
---

### Post by anonybart on 2016-08-06
Hello guys,
I read dozens of posts related to this problem but none of this has been able to help me fully.

I want to allow traffic only throught the domain (not only from port 80, also 9987 and more).
The main problem is after that the connections fell or that new connections could not access.

Thanks for the help!

---

### Post by SeijiSensei on 2016-08-06
If all the hosts in the "domain" are on one or a few IP subnets, you can just write rules that permit those address ranges and block everything else.  For instance,
```

/sbin/iptables -A INPUT -s 10.1.0.0/16 -d 10.1.0.0/16 -j ACCEPT
/sbin/iptables -A INPUT -j REJECT

```
This passes traffic between all the hosts with addresses in the range 10.1.0.0 and 10.1.255.255.  All other traffic is rejected.

If this box also needs to act as a router between networks, you must enable IP forwarding in /etc/sysctl.conf (instructions given there), and you may need some FORWARD iptables rules as well depending on what you set as the default "policies" in iptables.

---

