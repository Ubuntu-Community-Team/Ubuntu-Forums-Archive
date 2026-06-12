---
title: "Cron every 2 weeks"
date: 2009-12-21
forum: Server Platforms
---

### Post by dragos2 on 2009-12-21
How does a cron that needs to be executed every 2 weeks looks like ?

---

### Post by Grenage on 2009-12-21
```
*     *   *   *    0/2  commandhere
```

I think that's about right.  0=Sunday. /2 indicates every other.

---

### Post by dragos2 on 2009-12-21
> **Grenage said:**
> ```
*     *   *   *    0/2  commandhere
```I think that's about right.  0=Sunday. /2 indicates every other.

Thanks, and for midnight I would use it like this: ?

```

* 0 * *  0/2  commandhere

```

---

### Post by Grenage on 2009-12-21
Bingo :)

---

### Post by dragos2 on 2009-12-21
> **Grenage said:**
> Bingo :)

Lol thanks :)

---

