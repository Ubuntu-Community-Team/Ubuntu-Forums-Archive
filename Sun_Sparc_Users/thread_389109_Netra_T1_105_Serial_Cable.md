---
title: "Netra T1 105 Serial Cable"
date: 2007-03-20
forum: Sun Sparc Users
---

### Post by xneptuno on 2007-03-20
Hi,

When é unplug the serial cable from my sun netra t1 105 halts!

Already somebody had this type of problems? How to fix this?


Tks,

---

### Post by nemonoid on 2007-03-24
You should be able to disable it with this, but I haven't tested it myself. It does disable STOP-A on Sun keyboard which is equivalent to a BREAK over serial IIRC:

```
echo 0 > /proc/sys/kernel/stop-a
```

Let me know if this works for you!

--
nem

---

### Post by xneptuno on 2007-03-28
Hi nemonoid,

5 :KS

The system continues working when i unplug serial cable.


Tks!

---

### Post by xneptuno on 2007-05-01
Hi,


When I restart, return to the normal. It is that possible to define this definitively??

Something like: kernel.stop-a = 0 in /etc/sysctl.conf ?


Thanks,

---

