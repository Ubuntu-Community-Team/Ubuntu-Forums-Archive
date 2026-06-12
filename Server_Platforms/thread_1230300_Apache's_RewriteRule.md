---
title: "Apache's RewriteRule"
date: 2009-08-03
forum: Server Platforms
---

### Post by always_beginner on 2009-08-03
Hi,
I have my web directory like this:
 
/var/www/html
/var/www/cgi-bin
 
/var/www/html/js
/var/www/html/css
/var/www/html/html_doc
 
/var/www/html/html_doc/pattern1
/var/www/html/html_doc/pattern2
 
/var/www/html/html_doc/pattern1/index.html
/var/www/html/html_doc/pattern1/others
 
I set apache's root directory to /var/www/html, in this way, I will have to input url 'http://hostname/html_doc/pattern1/' to access my index.html, which is inconvenient. How can I set apache's rewriteRule to make it show the index.html when only input url as 'http://hostname/' ?
 
I tried 
RewriteRule ^(.*)$ /html_doc/pattern1/$1 [L]
 
but the cgi-file's path is also rewritten...
 
Any suggestioin will be welcome. thanks first.:)

---

### Post by cdenley on 2009-08-03
Maybe something like this:
```

RewriteRule ^/$ /html_doc/pattern1/index.html

```

---

### Post by always_beginner on 2009-08-03
> **cdenley said:**
> Maybe something like this:
```

RewriteRule ^/$ /html_doc/pattern1/index.html

```
 
I don't see the difference between this and mine:(
thanks anyway.

---

### Post by cdenley on 2009-08-03
> **always_beginner said:**
> I don't see the difference between this and mine:(
thanks anyway.

Your rule matches for any request, mine only for one (/).

---

