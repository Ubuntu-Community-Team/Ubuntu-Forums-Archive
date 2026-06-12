---
title: "linux-image-2.6.15-26-server upgrade forbidden"
date: 2006-09-14
forum: Repositories &amp; Backports
---

### Post by dgooding on 2006-09-14
I tried apt-get upgrading today and got a concerning message:

```
Err http://security.ubuntu.com dapper-security/main linux-image-2.6.15-26-server 2.6.15-26.47
  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-26-server_2.6.15-26.47_i386.deb  403 Forbidden
```

I noticed that the .46_i386.deb file was accesible though.  Thought someone should know...

---

### Post by dgooding on 2006-09-15
aaaand, the problem has gone away.  Thanks!

---

