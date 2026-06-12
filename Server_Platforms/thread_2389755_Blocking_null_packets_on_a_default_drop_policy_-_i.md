---
title: "Blocking null packets on a default drop policy - iptables"
date: 2018-04-21
forum: Server Platforms
---

### Post by faizan90 on 2018-04-21
If I have a default DROP policy on INPUT chain for iptables and then I have a rule that states:

-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT

Do I still need to add this rule for keeping bots scanning my server?

iptables -A INPUT -p tcp --tcp-flags ALL NONE -j DROP

---

### Post by The Cog on 2018-04-21
You don't generally need that second rule if your policy is DROP. 
Rules are evaluated in order. If your rules list only consists of ACCEPT rules for various things (this is common) then using the default drop policy to stop everything that is not explicitly ACCEPTed will be fine - it's probably what you want to do.

Unless you have complicated rules mixing ACCEPT and DROP lines in order to treat subgroups of things differently, that is. E.g:
    DROP packets from 10.1.5.11
    ACCEPT packets from the rest of 10.1.5.0/24

---

