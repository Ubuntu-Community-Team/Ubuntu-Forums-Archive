---
title: "Ufw rule delete"
date: 2011-03-03
forum: Server Platforms
---

### Post by dragos2 on 2011-03-03
How to delete this ufw rule in Ubuntu 8.04 :

```

To                         Action  From
--                         ------  ----

1521:tcp                   ALLOW   x.y.z.w

```

I tried this:
```

ufw delete allow proto tcp from x.y.z.w port 1521

```

---

