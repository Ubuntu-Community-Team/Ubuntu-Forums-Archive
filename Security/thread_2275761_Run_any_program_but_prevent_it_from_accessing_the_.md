---
title: "Run any program but prevent it from accessing the Internet"
date: 2015-04-28
forum: Security
---

### Post by r.lubken on 2015-04-28
Hi I'm trying to use this tutorial: [http://ubuntuforums.org/showthread.php?t=1188099&](http://ubuntuforums.org/showthread.php?t=1188099&)
to run any program but prevent it from accessing the Internet.
The tutorial works fine to block everything but if I would like to keep LAN access than I need to use this code as rule:
```
iptables -A OUTPUT -m owner --gid-owner no-internet -d ! 192.168.0.0/24 -j DROP
```
but if I do 
```
sudo /etc/network/if-pre-up.d/iptables_no-internet_rule
```
then I get:
```
Bad argument `192.168.0.0/24'
Try `iptables -h' or 'iptables --help' for more information.
```


any ideas?

---

### Post by Doug S on 2015-04-28
This:```
iptables -A OUTPUT -m owner --gid-owner no-internet -d [COLOR=#ff0000]![/COLOR] 192.168.0.0/24 -j DROP
```Should be this:```
iptables -A OUTPUT -m owner --gid-owner no-internet [COLOR=#ff0000]! [/COLOR]-d 192.168.0.0/24 -j DROP
```Notice the location of the exclamation (the "NOT" flag) mark. I have tested this reply on my system.

---

### Post by r.lubken on 2015-04-28
Okay that works! Thanks!

---

