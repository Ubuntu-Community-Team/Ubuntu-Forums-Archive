---
title: "apache2 serving up default if www not added to virtual host name"
date: 2014-08-04
forum: Server Platforms
---

### Post by wolfgang-rumpf on 2014-08-04
I'm not sure what I've done wrong here.  My default domain works fine.  My virtual host domains work fine as long as I type in the full url, e.g. "www.domain.com".  But if I type in just "domain.com" the default page is loaded.  Here's my domain.conf file, edited to obscure the actual domain:
[FONT=arial black]
<VirtualHost *:80>




        ServerName domain.com
        ServerAlias [www.domain.*]("http://www.domain.*") domain.*
        ServerAdmin [EMAIL="me@gmail.com"]me@gmail.com[/EMAIL]
        DocumentRoot /var/www/domain
</VirtualHost>[/FONT]

---

