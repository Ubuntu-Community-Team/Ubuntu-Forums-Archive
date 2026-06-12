---
title: "'ProxyPass / http://localhost:8000/' broke .htaccess redirects"
date: 2008-05-16
forum: Server Platforms
---

### Post by armware on 2008-05-16
I have a Ruby on Rails application setup behind Apache. Once I had setup proxypass:
```

ProxyPass / http://localhost:8000/
ProxyPassReverse / http://localhost:8000/

```

redirects in the .htaccess file no longer get redirected, and are replaced with rails' 404 page.
This also turned awstats into a 404, but once I added:
```

ProxyPass /awstats !

```

it became a '400 Bad Request' page.

Logs have shown nothing except the apache access log:
[16/May/2008:14:57:42 -0500] "GET /awstats HTTP/1.1" 400 313 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5"

Any have ideas? I'll sooo buy you a beer.

---

### Post by armware on 2008-05-16
Mongrel doesn't bother with .htaccess files.
How can I redirect within mongrel, or better yet, apache before the pass to mongrel?

---

