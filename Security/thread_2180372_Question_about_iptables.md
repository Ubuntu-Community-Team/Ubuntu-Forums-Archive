---
title: "Question about iptables"
date: 2013-10-12
forum: Security
---

### Post by Hungry Man on 2013-10-12
Is it possible to limit input to a user id?

I know you can use a rule like:

-A OUTPUT -p udp -m owner --uid-owner 116 -m udp --dport 443 -j ACCEPT

but can I do the same thing with input? What needs to change? I believe if I just change to INPUT it won't work.

---

### Post by unspawn on 2013-10-13
The following 'dmesg' line should show when trying to use the module in the filter table INPUT chain:
```
x_tables: ip_tables: owner match: used from hooks INPUT, but only valid from OUTPUT/POSTROUTING
```

---

