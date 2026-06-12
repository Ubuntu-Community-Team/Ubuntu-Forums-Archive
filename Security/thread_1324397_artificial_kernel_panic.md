---
title: "artificial kernel panic"
date: 2009-11-12
forum: Security
---

### Post by marwooj on 2009-11-12
How can I cause artificial kernel panic ?

---

### Post by __p1n__ on 2009-11-12
> **marwooj said:**
> How can I cause artificial kernel panic ?

Call the panic function.  You can pass a format string followed by some args if you want a message displayed.

If you're doing work at this level then you should know this already.

---

### Post by marwooj on 2009-11-12
> **__p1n__ said:**
> Call the panic function.  You can pass a format string followed by some args if you want a message displayed.

Will this stop system to respond?

---

