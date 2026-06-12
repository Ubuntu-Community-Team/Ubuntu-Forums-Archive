---
title: "Problem with Apache2"
date: 2009-04-27
forum: Server Platforms
---

### Post by Hadi Jadallah on 2009-04-27
Hi

I installed the new Server 9.04 64-bit edition of ubuntu on an IBM x3650 series server.
Everything appears to be running smoothly apart from one thing:
AcceptPathInfo is not working.
PHP5 is used in module mode...no CGI is running whatsoever.
I tried putting the directive AcceptPathInfo On everywhere
Tried the vhost/directory/mod_rewrite/...etc
Tried the httpd.conf
tried the .htacess
but nothing seems to work.

Any ideas?

---

### Post by Hadi Jadallah on 2009-04-28
Hi

Problem solved....
Proxy was missing around with some of the header variables.

---

