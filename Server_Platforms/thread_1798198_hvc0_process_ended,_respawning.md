---
title: "hvc0 process ended, respawning"
date: 2011-07-06
forum: Server Platforms
---

### Post by vpswing on 2011-07-06
Hello Everyone,

I'm getting this "error" logged in the /var/log/syslog
--------
Jul  6 02:46:26 srv1 init: hvc0 main process (21769) terminated with status 1
Jul  6 02:46:26 srv1 init: hvc0 main process ended, respawning

Jul  6 02:46:36 srv1 init: hvc0 main process (21771) terminated with status 1
Jul  6 02:46:36 srv1 init: hvc0 main process ended, respawning

-------------

It's happening every 10 seconds .... any idea how to fix this?

I'm on a Xen VPS, running Ubuntu server 10.04.


Many thanks!

---

### Post by vpswing on 2011-07-06
Digging further, I found this config file in /etc/init

hvc0.conf:

---------------------------------------------
start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/getty -8 38400 hvc0
---------------------------------------------

Do I need this "hvc0" ? Can I safely remove it? 

Thanks!

---

### Post by hackeron on 2012-05-03
Having the same issue :( - anyone?

---

