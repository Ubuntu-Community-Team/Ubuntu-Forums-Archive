---
title: "drbd module missing from 64bit server kernel?"
date: 2009-09-15
forum: Server Platforms
---

### Post by SergeiFranco on 2009-09-15
Hi,
this is really odd, as the drbd module is in the /lib/modules/2.6.28-8-generic/kernel/ubuntu/drbd/drbd.ko
but not in the 2.6.28-15-server

How do I install drbd8 in server?

---

### Post by SergeiFranco on 2009-09-15
Actually it looks like virtual kernel reports itself as server hence the confusion....

---

### Post by cariboo on 2009-09-15
I just checked my install:

```
Linux willy 2.6.28-15-server #49-Ubuntu SMP Tue Aug 18 20:09:37 UTC 2009 x86_64 GNU/Linux
```

it has the drbd module in /lib/modules/2.6.28-15-server/kernel/ubuntu/drbd

---

### Post by SergeiFranco on 2009-09-15
I did install server kernel (it had virtual but reported as server in uname -r and every where), and there was drbd module.

---

### Post by cariboo on 2009-09-15
It looks like we posted at the same time. :)

---

