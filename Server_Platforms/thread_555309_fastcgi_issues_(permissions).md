---
title: "fastcgi issues (permissions)"
date: 2007-09-20
forum: Server Platforms
---

### Post by xIke on 2007-09-20
When I run apache2 -S, it complains:
```

Syntax error on line 4 of /etc/apache2/mods-enabled/fastcgi.conf:
FastCgiIpcDir /var/lib/apache2/fastcgi: access for server (uid 1000, gid 1000) failed: write not allowed
```
But if I change this, apache2 will no longer start, complaining that these need to be user 33, group 33.

Any ideas how I can resolve this?

---

