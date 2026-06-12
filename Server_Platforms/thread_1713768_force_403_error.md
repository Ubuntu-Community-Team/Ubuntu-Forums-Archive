---
title: "force 403 error"
date: 2011-03-24
forum: Server Platforms
---

### Post by wiggly81 on 2011-03-24
hi, 

I would like to force a 403 error to show up when sub.domain.com (Apache server) is used to access my site, I know I could probably create a virtual host making the sub domain point to a file that has not read / write perms but I figure there must be a better way to do this with mod_rewrite or something just not sure how I would do it.

thanx in advance

---

### Post by falko on 2011-03-24
Try this:

```
RewriteCond %{HTTP_HOST} ^sub.domain.com [NC]
RewriteRule .* - [F]
```

---

### Post by wiggly81 on 2011-03-24
Perfect Thank you.

---

