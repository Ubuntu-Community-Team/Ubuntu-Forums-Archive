---
title: "faxgetty on startup (Hylafax on Edgy)"
date: 2006-12-15
forum: Server Platforms
---

### Post by cyberbaga on 2006-12-15
Hi all,
I'am trying to setup hylafax-server 4.3 (default package) on edgy but i'have a question:

In order to receive external fax  (from startup) in previous ubuntu release i must add on /etc/inittab the following line

S0:2345:respawn:/usr/sbin/faxgetty ttyS0

How i can do it for setting faxgetty on startup in edgy / upstart ?

I've tried to copy a tty1 job and modify with faxgetty but no result.

Thanks

---

### Post by pat2man on 2007-09-17
FYI for anyone reading this, the following worked for me:


```
start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /usr/sbin/faxgetty ttyIAX
```

---

