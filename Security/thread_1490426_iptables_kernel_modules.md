---
title: "iptables kernel modules"
date: 2010-05-22
forum: Security
---

### Post by eXDee on 2010-05-22
Short and simple.

What kernel modules are required for the use of "string"?
```
iptables -I INPUT -p tcp --dport 123 -m string --algo kmp --string "blahblahblah" -j CHAIN
```

causes
```
FATAL: Could not load /lib/modules/2.6.18-128.2.1.el5.028stab064.4/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-128.2.1.el5.028stab064.4/modules.dep: No such file or directory
iptables: No chain/target/match by that name.
```

This is on an OpenVZ VPS. The host will load the modules on the node if we tell them what to load, but i have no idea what it is.

We also get this error when we try and use hashlimit too. Yet all basic iptables functions work fine.

Cheers.

---

### Post by bodhi.zazen on 2010-05-22
Openvz VPS have limited support for iptables and do not use strings.

See : [http://wiki.openvz.org/Setting_up_an_iptables_firewall](http://wiki.openvz.org/Setting_up_an_iptables_firewall)

If you search the openvz forum you will find additional discussions on IPTABLES.

Or google search iptables strings linux kernel.

The bottom line, as I indicated, not all iptables modules work in Openvz guests, and strings is one that is broken or not yet implemented .

---

