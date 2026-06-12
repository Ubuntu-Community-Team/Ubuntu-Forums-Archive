---
title: "Apache 2: ServerAlias that conflicts with ServerName"
date: 2010-07-07
forum: Server Platforms
---

### Post by mschipperheyn on 2010-07-07
Hi,

I have a Tomcat integrated site that uses city names as sub domains (amsterdam.site.nl, rotterdam.site.nl, etc)
However, now I want to create a separate virtual host to serve assets: assets.site.nl

I'm running into some problems trying to configure this.
[PHP]
site 1
NameVirtualHost *:80
<VirtualHost *:80>
	ServerName www.site.nl	
	ServerAlias *.site.nl
        ServerAdmin webmaster@site.nl

        DocumentRoot /usr/share/ROOT/
		
	JkMount //* ajp13_worker [double // because single causes post to this forum to fail]
	JkUnMount //*.jpg ajp13_worker
		
        ServerSignature On
</VirtualHost>
site2
NameVirtualHost *:80
<VirtualHost *:80>
	ServerName assets.site.nl	
        ServerAdmin webmaster@site.nl

        DocumentRoot /usr/share/ROOT/
		
        ServerSignature On
</VirtualHost>
[/PHP]

When I enable site 2, I get no error message in the error log.
[www.site.nl/images/test.jpg](www.site.nl/images/test.jpg) and amsterdam.site.nl/images/test.jpg both work
but the sites ajp worker for site 1 doesn't seem to work anymore as the normal pages (/*.html etc) are no longer returned

Any ideas on how to handle this?

Kind regards,
Marc

---

### Post by souki on 2010-07-07
only one 'NameVirtualHost' directive per IP/Port is allowed
[http://httpd.apache.org/docs/2.0/mod/core.html#namevirtualhost](http://httpd.apache.org/docs/2.0/mod/core.html#namevirtualhost)

---

