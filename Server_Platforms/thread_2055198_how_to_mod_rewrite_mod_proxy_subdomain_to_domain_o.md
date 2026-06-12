---
title: "how to mod_rewrite mod_proxy subdomain to domain on apache2 + tomcat - java server"
date: 2012-09-08
forum: Server Platforms
---

### Post by 007casper on 2012-09-08
how to mod_rewrite mod_proxy subdomain to domain on apache2 + tomcat - java server

I am running on tomcat server that has webapps listening on 8080

I would like the server to 
1 - Grab the wild subdomain from the domain
2 - Make sure the subdomain is not www, w or ww
3 - Check if the directory actually exists on "www.domain.com" before rewrite
4 - if the directory doesnt exist it stays as wild domain
5 - Finally, if the directory exist the actual rewrite

I couldnt make it work with mod_rewrite alone.  I have been looking into
mod_proxy, mod_proxy_ajp, and mod_rewrite

?

---

### Post by sandyd on 2012-09-08
***moved to server platforms***

---

