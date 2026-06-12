---
title: "Find network devices"
date: 2011-01-18
forum: Security
---

### Post by mark1969 on 2011-01-18
Hello, I am connected to the internet through a wireless router. The router has other devices connected to it both wired and wireless. I am trying to find what other devices are connected at any one time and also keep a log and alert me if a device connects or disconnects. I know I can view the connections by going to the routers config page but there is no way to set alerts or keep a log. Can anyone suggest a fairly straightforward way of doing this.
Thanks

---

### Post by artie_effim on 2011-01-18
If the router supports SNMP you could configure an alert system on your mgmt box.  That is the best way.

Or else you could do a ping sweep of the DHCP subnet every 5 minutes, pass it through `watch` and if there are differences watch can be made to highlight them.  read man pages for ping and watch.

---

