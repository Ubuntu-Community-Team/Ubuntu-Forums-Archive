---
title: "Do me a favour please?"
date: 2009-10-06
forum: The Cafe
---

### Post by kevin11951 on 2009-10-06
Can someone do me a favour and ping [www.kviero.com](www.kviero.com), crm.kviero.com, cms.kviero.com.  Tell me what the IP addresses are that show up.

---

### Post by doas777 on 2009-10-06
```

** server can't find www.kviero.com/: NXDOMAIN

```edit: now I'm getting it. missed that slash on the end:

Non-authoritative answer:
[www.kviero.com]("http://www.kviero.com")    canonical name = kviero.com.
Name:    kviero.com
Address: 99.20.92.234

Non-authoritative answer:
Name:    crm.kviero.com
Address: 99.20.92.234

Non-authoritative answer:
Name:    crm.kviero.com
Address: 99.20.92.234


so, why aren't you doing this yourself with nslookup or dig?

---

### Post by cguy on 2009-10-06
PING kviero.com (99.20.92.234) 56(84) bytes of data.

---

### Post by kevin11951 on 2009-10-06
> **doas777 said:**
> [code]

so, why aren't you doing this yourself with nslookup or dig?

because when I ping it, it comes up as 192.168.2.2, and I wanted to make sure it didnt do that outside my router.

---

### Post by OpenGuard on 2009-10-06
```
PING kviero.com (99.20.92.234) 56(84) bytes of data.
PING crm.kviero.com (99.20.92.234) 56(84) bytes of data.
PING cms.kviero.com (99.20.92.234) 56(84) bytes of data.

```

---

