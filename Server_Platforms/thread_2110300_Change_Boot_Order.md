---
title: "Change Boot Order"
date: 2013-01-29
forum: Server Platforms
---

### Post by Code9 on 2013-01-29
I recently had a problem where a service was not starting because

```

Failed initialization: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'

```

I believe this is because MySQL has not yet started when this is called. I am wondering if I should try to change the boot order.

---

