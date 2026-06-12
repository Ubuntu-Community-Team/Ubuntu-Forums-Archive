---
title: "Run server on UTC?"
date: 2007-03-25
forum: Server Platforms
---

### Post by graylion on 2007-03-25
Hi folks I have a server running on Dapper and it duly performed the switch to DST - only i don't want it to! IMO Servers should run on UTC and be done with. How can I stop Ubuntu from switching?

---

### Post by Mr. C. on 2007-03-25
You are confused.  All internal Unix/Linux times are UTC times.

What you see as output from programs, etc. is converted to localtime, which is controlled by either the TZ variable or /etc/localtime.

Convince yourself:

```
$ date
Sun Mar 25 16:00:06 PDT 2007
$ TZ=GMT date    
Sun Mar 25 23:00:34 GMT 2007
$ TZ=EDT date
Sun Mar 25 23:00:57 EDT 2007
```

MrC

---

