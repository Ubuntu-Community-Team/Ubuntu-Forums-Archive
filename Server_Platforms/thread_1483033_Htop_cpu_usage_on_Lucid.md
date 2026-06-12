---
title: "Htop cpu usage on Lucid"
date: 2010-05-14
forum: Server Platforms
---

### Post by dragos2 on 2010-05-14
Anyone noticed that the htop package for Lucid is consuming much more CPU than the
version for Hardy ?

---

### Post by kimberlite on 2010-05-14
It eats up 1-2 % of my Intel Core CPU (T5550 @ 1.83GHz) on Lucid. I do not know how it would perform on Hardy.

---

### Post by cdenley on 2010-05-14
You could always increase the time between polls to reduce CPU usage.
```

htop -d 30

```

---

