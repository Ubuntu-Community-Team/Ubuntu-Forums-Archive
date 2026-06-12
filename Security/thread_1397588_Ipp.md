---
title: "Ipp"
date: 2010-02-03
forum: Security
---

### Post by bbourdet on 2010-02-03
Is there a problem having port 631 for IPP open? Any security issues I should know about? A quick google search does not bring anything up.

Your thoughts?


Tarken

---

### Post by cdenley on 2010-02-03
Cups should bind to the local interface (127.0.0.1) by default. There is usually no reason to allow people to connect to CUPS remotely.
```

sudo netstat -tlnp

```

---

