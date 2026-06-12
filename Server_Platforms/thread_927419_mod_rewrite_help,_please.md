---
title: "mod_rewrite help, please"
date: 2008-09-22
forum: Server Platforms
---

### Post by mexlinux on 2008-09-22
Hi:
I want to change my urls this way:
```

http://www.mysite.com/search.php?q?some queries

to

http://www.mysite.com/search/some queries


```


I have created a .htaccess with the following:
```

RewriteEngine on
RewriteRule ^search/([^/\.]+) index.php?q=$1&ac=Find+Movie [L]

```

In principle, It works, but once i access 
[http://www.mysite.com/search/some](http://www.mysite.com/search/some) queries

All my urls and references are broken, because now the "directory" search is at the begining of my references,
therefore, for example the url:

[http://www.mysite.com/search/logo.png](http://www.mysite.com/search/logo.png) does not exists
                      ******


How to avoid this?

---

