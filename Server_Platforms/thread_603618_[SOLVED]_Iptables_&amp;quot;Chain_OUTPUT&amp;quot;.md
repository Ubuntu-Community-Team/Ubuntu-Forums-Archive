---
title: "[SOLVED] Iptables &amp;quot;Chain OUTPUT&amp;quot; query"
date: 2007-11-05
forum: Server Platforms
---

### Post by Absorbed on 2007-11-05
I have a quick query concerning iptables. When I type "sudo iptables -L -n", the following is included in the output:

```
Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  10.0.0.6             10.0.0.2            tcp dpt:53 
ACCEPT     udp  --  10.0.0.6             10.0.0.2            udp dpt:53
```

.6 is my computer and .2 is my router. I am wondering what this is. Are these rules standard?

---

### Post by MJN on 2007-11-05
I don't use iptables but I can tell you what the rules are doing - they are allowing TCP and UDP packets from your machine to the router on port 53. Port 53 is used by DNS and hence these rules must have been added by something to allow you to make DNS queries from your machine (to your router which likely acts as an intermediary for your DNS queries).

No rules are usually 'standard' in a firewall - something/someone must have added them.

Mathew

---

### Post by Absorbed on 2007-11-05
> **MJN said:**
> I don't use iptables but I can tell you what the rules are doing - they are allowing TCP and UDP packets from your machine to the router on port 53. Port 53 is used by DNS and hence these rules must have been added by something to allow you to make DNS queries from your machine (to your router which likely acts as an intermediary for your DNS queries).

No rules are usually 'standard' in a firewall - something/someone must have added them.

Mathew

Thanks. It is DNS. I removed my DNS settings in System->Settings and the rules disappeared after a reboot, and the same again to get them back again.

---

