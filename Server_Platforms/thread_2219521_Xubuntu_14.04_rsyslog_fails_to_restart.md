---
title: "Xubuntu 14.04 rsyslog fails to restart"
date: 2014-04-24
forum: Server Platforms
---

### Post by peter3 on 2014-04-24
[SOLVED]
On performing 
# /etc/init.d/rsyslog force-reload
nothing happens and the conf files do not re-read.
In fact, NONE of the choices for /etc/init.d/rsyslog do anything.
Otherwise the new install seems to work fine.
PS.  Any help on searching the forums for this answer would be greatly appreciated.

the proper command is now
service rsyslog restart

---

