---
title: "Unkown entry in my IPtables.  Help please"
date: 2009-07-03
forum: Security
---

### Post by csalsb on 2009-07-03
Folks

I just built a ubuntu server 9.04 and built my own iptables and scripts.  However when I run Iptables -L I get all my rules like expected.  However, I get one rule that is clearly not in my iptable script.  This is the rule that I can't figure out what is inserting it into my firewall

ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:http-alt

If someone could shed some light on this for me I would greatly appreciate it.  Is it something that Ubuntu is doing whith one of there scripts or do I need to be concerned.

csalsb

---

### Post by bodhi.zazen on 2009-07-03
run

```
iptables -l -v
```The -v will give you more information.

From there we need to know how you configured iptables since by default iptables is not configured.

Since you use your own script perhaps it would help if you posted your script.

---

### Post by The Cog on 2009-07-03
FYI, http-alt is port 8080, commonly used by proxy servers. Could it be that you specified this port by number, and it is now showing it back by name?

---

### Post by csalsb on 2009-07-03
Yep that is it I did configure Port 8080.  That is exactly what is going on.  Thanks for the assist I appreciate it.

csalsb

;)

---

