---
title: "Ubuntu Server Apache2 SSL virtual host not working"
date: 2014-03-20
forum: Server Platforms
---

### Post by kmccmk9 on 2014-03-20
[COLOR=#333333][FONT=UbuntuRegular]I have fully set up a web server on ubuntu using SSL encryption. I am trying to set up the default -SSL file to point to the correct directories. geekychicgirls works completely fine, however [www.thepeepinghole](www.thepeepinghole) always resolves to geekychicgirls and [www.geekychicgirls](www.geekychicgirls) resolves to thepeepinghole, any help is appreciated see code below.

```

[/FONT][/COLOR]<IfModule mod_ssl.c>
<VirtualHost *:443>
    ServerAdmin webmaster@nixcraft.com
    DocumentRoot "/var/www/thepeepinghole"
    SSLEngine on
    SSLCertificateFile /ssl/14252798.crt
    SSLCertificateKeyFile /ssl/private.key
    SSLCertificateChainFile /ssl/futureretrogaming.ca-bundle
    ServerName www.thepeepinghole.tk
    ServerAlias thepeepinghole.tk
    ErrorLog "/var/www/thepeepinghole/log/error.log"
    CustomLog "/var/www/thepeepinghole/log/access.log" common
    <Directory /var/www/thepeepinghole>
                DirectoryIndex index.html
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
     </Directory>
</VirtualHost>

<VirtualHost *:443>
    ServerAdmin webmaster@nixcraft.com
    DocumentRoot "/var/www/geekychicgirls"
    SSLEngine on
    SSLCertificateFile /ssl/14252798.crt
    SSLCertificateKeyFile /ssl/private.key
    SSLCertificateChainFile /ssl/futureretrogaming.ca-bundle
    ServerName www.geekychicgirls.tk
    ServerAlias geekychicgirls.tk
    ErrorLog "/var/www/geekychicgirls/log/error.log"
    CustomLog "/var/www/geekychicgirls/log/access.log" common
    <Directory /var/www/geekychicgirls>
                DirectoryIndex index.html
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
     </Directory>
</VirtualHost>

</IfModule>[COLOR=#333333][FONT=UbuntuRegular]
```
[/FONT][/COLOR]

---

### Post by TheFu on 2014-03-20
You cannot have 2 SSL virtualhosts using the Name-based virtualhost method and default SSL libraries.
A few years ago, I read about GNUTLS supporting this, but I've never tried it myself. [http://www.howtoforge.com/hosting-multiple-ssl-web-sites-on-one-ip-address-with-apache-2.2-and-gnutls-debian-lenny](http://www.howtoforge.com/hosting-multiple-ssl-web-sites-on-one-ip-address-with-apache-2.2-and-gnutls-debian-lenny)

What I would do is .... Setup a generic domainname and put SSL on it, then setup any other domains to redirect from HTTP to specific directories on that other domain.  

geekychicgirls.tk --> example.com/gcg/
thepeepinghole.tk --> example.com/tpph/

Does this make sense?

Or you could use subdomains from the same TLD.
* gcg.example.com
* tpph.example.com
and get a wildcard SSL cert for *.example.com, install that on a front-end reverse proxy, and redirect to back-end systems without the SSL.
Ref: [https://wiki.apache.org/httpd/NameBasedSSLVHosts](https://wiki.apache.org/httpd/NameBasedSSLVHosts)

Or you can add an IP address to the server and use it for the other domain. 1 IP = 1 SSL cert.

---

### Post by kmccmk9 on 2014-03-20
> **TheFu said:**
> You cannot have 2 SSL virtualhosts using the Name-based virtualhost method and default SSL libraries.
A few years ago, I read about GNUTLS supporting this, but I've never tried it myself. [http://www.howtoforge.com/hosting-multiple-ssl-web-sites-on-one-ip-address-with-apache-2.2-and-gnutls-debian-lenny](http://www.howtoforge.com/hosting-multiple-ssl-web-sites-on-one-ip-address-with-apache-2.2-and-gnutls-debian-lenny)

What I would do is .... Setup a generic domainname and put SSL on it, then setup any other domains to redirect from HTTP to specific directories on that other domain.  

geekychicgirls.tk --> example.com/gcg/
thepeepinghole.tk --> example.com/tpph/

Does this make sense?

Or you could use subdomains from the same TLD.
* gcg.example.com
* tpph.example.com
and get a wildcard SSL cert for *.example.com, install that on a front-end reverse proxy, and redirect to back-end systems without the SSL.
Ref: [https://wiki.apache.org/httpd/NameBasedSSLVHosts](https://wiki.apache.org/httpd/NameBasedSSLVHosts)

Or you can add an IP address to the server and use it for the other domain. 1 IP = 1 SSL cert.

Ok I don't think I fully understand. I purchased a ssl script that supports up to 10 unique domain names...what's the point of that if I have to do what you said which is one domain name for them all and use a bunch of redirects and pointers?

---

### Post by TheFu on 2014-03-20
> **kmccmk9 said:**
> Ok I don't think I fully understand. I purchased a ssl script that supports up to 10 unique domain names...what's the point of that if I have to do what you said which is one domain name for them all and use a bunch of redirects and pointers?

How can I possibly answer your question?  Talk to the people who sold you that script.  I think you've been sold snakeoil, until someone else proves me wrong. Sorry.  I could be wrong, but ... don't think so.

I'm only providing the best answers based on 20+ yrs of doing this stuff.

---

