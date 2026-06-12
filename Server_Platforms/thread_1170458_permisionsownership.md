---
title: "permisions/ownership"
date: 2009-05-26
forum: Server Platforms
---

### Post by lex1 on 2009-05-26
have cgi-bin and cgi-data in /www/var/ they have to be moved to /var/www/modified cgi-data has to be owned by webserver(www-data) cgi-bin owned by root but readable webserver www-data

how can this be accomplished

lex1;)

---

### Post by cdenley on 2009-05-26
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
```

man chown
man chmod

```

---

