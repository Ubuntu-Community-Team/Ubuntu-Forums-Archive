---
title: "unblocking ports..."
date: 2007-02-20
forum: Ubuntu Christian Edition
---

### Post by sinisterguy on 2007-02-20
Hello,

i recently installed the ubuntu CE packages for dansguardian and the gui and it seems that iptables was intalled as well. I frequently need to access my home system from school so I installed ssh and its running on a non-standard port (port 99, the school blocks most standard ports). it seems the firewall is stopping me from gaining access to my system. I tried doing this: iptables -A INPUT -p tcp -i ra0 --dport 99 -j ACCEPT but its still blocking me. Any suggestions?

---

