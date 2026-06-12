---
title: "Does this script close off all other scripts?"
date: 2018-09-06
forum: Security
---

### Post by webmiester on 2018-09-06
I read in an online article that there were many mikrotik routers that were hijacked and it appears that particular ports were most vulnerable (I think it was port 21, 21, 101, 145)...  Well Im using ubuntu and not mikrotik, but I figured it must be a good idea to close all the ports I dont need for security purposes.

If I open let's say port 80 with:

/sbin/iptables -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT

and then
I put the lines:

/sbin/iptables -A OUTPUT -j DROP
/sbin/iptables -A INPUT -j DROP

Does this close all the ports except for port 80, or do I need a different command to do that?

Thanks so much

---

