---
title: "Question about POSTFIX and pickup process"
date: 2017-02-15
forum: Server Platforms
---

### Post by simmete on 2017-02-15
Ciao,
quick question about the pickup process in postfix mail server:
In one I see the sender is ubuntu:
```
Feb 15 22:52:25 localhost postfix/pickup[28424]: 7B83044490: uid=33 from=<ubuntu>

```
In another I see the sender is ubuntu@localhost:
```
Feb 15 22:52:25 localhost postfix/pickup[28424]: 7B83044490: uid=33 from=<ubuntu@localhost>

```

Any suggestion to check where he gets the name from?
Thank you!

---

### Post by TheFu on 2017-02-19
The "from" means nothing. It can be set to any value - want a message from dog or god?  Fine.  Chances are there are different processes reading different config files to get the value for the 2nd one. The first 1 is probably pulling it from the passwd db.

UID 33 seems to be consistently www-data, so I'd assume some apache process is doing the sending.

---

