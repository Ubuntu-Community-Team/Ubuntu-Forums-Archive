---
title: "rp_filter why cant dsiable? premission denied"
date: 2011-04-29
forum: Server Platforms
---

### Post by newtonparadox on 2011-04-29
I am setting up WCCPV2 with squid with my ASA Box. I need to disable RP Filter with the following commands.

echo 0 >/proc/sys/net/ipv4/conf/wccp0/rp_filter 
echo 0 >/proc/sys/net/ipv4/conf/eth0/rp_filter


When i run them as sudo i get a permission denied.
Anyone have ideas?

---

### Post by newtonparadox on 2011-04-29
nevermind i realized i just need to look another the

sysctl.conf

---

