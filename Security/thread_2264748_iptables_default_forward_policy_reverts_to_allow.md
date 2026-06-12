---
title: "iptables default forward policy reverts to allow"
date: 2015-02-09
forum: Security
---

### Post by ODTech on 2015-02-09
I have a working ubuntu firewall/dhcp server/gateway.

The only issue is that the default forward policy always reverts to ACCEPT and i need it to stay on DROP.
I'm using iptables-persistent to load the rule set at bootup. The rule set in /etc/iptables/rules.v4 is correctly set to DROP for the FORWARD chain.

Is there anywhere else i can check for defaults that iptables-persistant might be looking at or should i rather use iptables-save and add a startup script for iptables-restore?

Thanks in advance

---

### Post by wannabe user on 2015-02-10
See if there's anything offending in /etc/default/iptables?

---

