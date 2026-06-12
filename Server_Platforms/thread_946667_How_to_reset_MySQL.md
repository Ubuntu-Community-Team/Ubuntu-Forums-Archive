---
title: "How to reset MySQL"
date: 2008-10-13
forum: Server Platforms
---

### Post by Epifrin on 2008-10-13
Sorry for making two threads at a time, but I'm still new at local web development.

So, I forgot my MySQL username & password and want to reset MySQL and all the databases it contains. How do I do so? Thanks. :)

---

### Post by lykwydchykyn on 2008-10-13
You could just purge the package and reinstall, if you don't want to save any tables or anything.
```

sudo aptitude purge mysql-server-5.0
sudo rm -Rf /var/lib/mysql
sudo aptitude install mysql-server-5.0

```

---

### Post by Rocketeer on 2012-01-25
[deleted] wrong forum.

---

