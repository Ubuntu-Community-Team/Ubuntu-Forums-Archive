---
title: "Forward all https:// requests to http://"
date: 2005-12-06
forum: Server Platforms
---

### Post by OneSeventeen on 2005-12-06
I know the common thing is to forward http:// to [https://,](https://,) but I am migrating a tool from a server with https:// to a server without.

How do I redirect users going to [https://foo.example.com](https://foo.example.com) to [http://foo.example.com](http://foo.example.com) ?

---

### Post by amohanty on 2005-12-06
UYse rewrite rules:

[http://httpd.apache.org/docs/trunk/misc/rewriteguide.html](http://httpd.apache.org/docs/trunk/misc/rewriteguide.html)

HTH

---

### Post by mgor on 2005-12-06
[https://wiki.ubuntu.com/forum/server/apache2/SSL](https://wiki.ubuntu.com/forum/server/apache2/SSL)

just change the rule to
```
RewriteEngine   on
RewriteCond     %{SERVER_PORT} ^80$
RewriteRule     ^(.*)$ https://%{SERVER_NAME}$1 [L,R]
RewriteLog      "/var/log/apache2/rewrite.log"
RewriteLogLevel 2
```

---

