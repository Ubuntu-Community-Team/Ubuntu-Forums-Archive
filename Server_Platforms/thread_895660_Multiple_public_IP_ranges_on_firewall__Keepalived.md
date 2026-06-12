---
title: "Multiple public IP ranges on firewall / Keepalived"
date: 2008-08-20
forum: Server Platforms
---

### Post by theh1982 on 2008-08-20
Hi,

I have currently a setup which contains a /27 range of 89.XX ip-addresses. I am using Ubuntu as my firewall ,now i received a new /26 range of 77.XX ip adddresses and i want to configure them as well on the same port in my firewallscript and keepalive config. Using eth0:1 is not working using IP-Tables and eth0 already has 1 89.XX ip assigned to itself.

Any suggestions on how to get this configuration working ?

---

### Post by Ximbiot on 2008-08-20
iptables will apply any eth0 rules to any virtual interfaces attached to eth0 (eth0:0, eth0:1, ...).

You can also filter it separately using the new IP range, like `-d 77.xx.xx.xx/26'.  So, to just accept all packets to the two ranges would require something like:

```
iptables -A INPUT -i eth0 -d 89.xx.xx.xx/27 -j ACCEPT
iptables -A INPUT -i eth0 -d 77.xx.xx.xx/26 -j ACCEPT
```

If that still doesn't answer your question, you might try googling "iptables virtual interface" for other options.

---

