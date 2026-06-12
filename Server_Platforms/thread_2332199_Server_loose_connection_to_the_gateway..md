---
title: "Server loose connection to the gateway."
date: 2016-07-29
forum: Server Platforms
---

### Post by spyker2 on 2016-07-29
Hi All,

I have the weird issue that I just can't figure out. I have an Cisco SG500 switch that is set to L3. The gateway is pointing to the switch ip all good. I can ping all the vlan traffic across the site. But after +- 30 minutes then you can't ping the switches of any of the vlan's. I can ping internet and internal vlan 1 no problem. Firewall is switch off.

Setup are as follow Ubuntu server 14.04 vm on Hyper-V 2012 R2 stand alone.

Any advise will be greatly appreciated!

Regards
Gerrit

---

### Post by Graham_Willis on 2016-07-31
Just guesses:

- are you really sure that all the firewalls that could possibly block these requests are turned off?
- perhaps it works the other way-round. Perhaps with these firewalls missing, there are (D)DoS on these switches and it's from where the problems arise?

When such a situation occurs it's possible to ping switches not responding to pings from themselves at least?

---

