---
title: "squid3 cache_dir in different partition problem"
date: 2012-08-15
forum: Security
---

### Post by !! hack-back !! on 2012-08-15
hi! i managed to install and can successfully start squid when it's  using the default cache_dir (/var/spool/squid). but when i changed the  cache_dir to a separate partition the squid says it is worked but its not
the /cache/ directory is already owned by the squid user and has  710 permission, just like the permission of /var/cache/squid.

what else could be the problem?
thanks

---

### Post by !! hack-back !! on 2012-08-15
cache.log says

2012/08/15 08:43:47| Rebuilding storage in /c1 (DIRTY)
2012/08/15 08:44:36| Rebuilding storage in /c2 (DIRTY)
2012/08/15 08:45:24| Rebuilding storage in /c3 (DIRTY)
2012/08/15 08:46:12| Rebuilding storage in /c4 (DIRTY)
2012/08/15 08:47:00| Rebuilding storage in /c5 (DIRTY

---

### Post by !! hack-back !! on 2012-08-15
help please

---

### Post by !! hack-back !! on 2012-08-15
any help ?????

---

