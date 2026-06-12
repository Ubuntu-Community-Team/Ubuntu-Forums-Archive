---
title: "Subdomain Redirect"
date: 2007-06-18
forum: Server Platforms
---

### Post by scottfinman on 2007-06-18
[LIST=1]
[*]How would one redirect all requests for [http://domain.com](http://domain.com) to [http://www.domain.com](http://www.domain.com) using apache VirtualHost's or mod_rewrite?
[*]Similarly, how would one redirect all requests for [http://www.subdomain.domain.com/](http://www.subdomain.domain.com/) to [http://subdomain.domain.com?](http://subdomain.domain.com?)
[/LIST]

---

### Post by Mr. C. on 2007-06-19
1)  If the domain is a virtual host already, you can just add a ServerAlias directive in the virtual host container:

```
    ServerAlias domain.com www.domain.com
```

For mod_rewrite, see Canonical Hostnames in:

   [http://httpd.apache.org/docs/1.3/misc/rewriteguide.html](http://httpd.apache.org/docs/1.3/misc/rewriteguide.html)

Of course, both of these presume you have a www A record for the domain.

2) The same principal applies with ServerAlias here too.

For mod_rewrite to change:
[http://www.subdomain.domain.com/](http://www.subdomain.domain.com/) to [http://subdomain.domain.com?](http://subdomain.domain.com?)

```
RewriteRule   ^www\.subdomain\.domain\.com/(.*)/$    subdomain.domain.com$1  [R]
```

or more generally:

```
RewriteRule   ^www\.(.*)$    $1  [R]
```

You can also use .htaccess redirects too.

MrC

---

### Post by scottfinman on 2007-06-19
Thanks Mr. C!

---

