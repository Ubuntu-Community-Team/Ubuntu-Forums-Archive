---
title: "HAProxy init.d script starts in foreground"
date: 2009-04-23
forum: Server Platforms
---

### Post by flyjedi on 2009-04-23
On a fresh install of Ubuntu 8.04, I ran:
```
apt-get install haproxy
```
setup my configuration as I would normally, and then:
```
/etc/init.d/haproxy start
```
and it starts however it runs in the forground?

To get it to start, i'm having to fork it:
```
/etc/init.d/haproxy start &
```

This also means that the boot process is hanging at HAProxy. I have to ssh in, kill the HAProxy process, and boot continues.

How do I make it start nicely?

---

