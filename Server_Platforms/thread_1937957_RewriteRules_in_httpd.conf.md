---
title: "RewriteRules in httpd.conf"
date: 2012-03-08
forum: Server Platforms
---

### Post by Engammalsko on 2012-03-08
Hi! I can't use RewriteRules on my apache server on the httpd.conf files I can redirect and RewriteRules works good in the .htaccess file.

```
works only on .htaccess
RewriteEngine On
RewriteRule ^/test$ /guestbook.php

#works on both .htaccess and httpd.confg
Redirect /test /guestbook.php
```

So what could be wrong? I don't get any errors. I'm restarting apache everytime I'm changing something. When I try to go to localhost/test I just get 404.

Please help me, I really can't figure this out. Tell me if you need to see the context files or anything to be able to help me.

---

### Post by SeijiSensei on 2012-03-10
I'm pretty sure that in a Redirect, the second argument needs to be a complete URL.

```
Redirect /test http://www.example.com/guestbook.php
```

---

