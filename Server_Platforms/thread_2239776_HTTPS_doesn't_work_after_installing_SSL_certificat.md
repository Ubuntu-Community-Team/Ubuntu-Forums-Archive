---
title: "HTTPS doesn't work after installing SSL certificate"
date: 2014-08-15
forum: Server Platforms
---

### Post by Maheriano on 2014-08-15
I followed a bunch of different tutorials for installing SSL certificates on my domain and they all seemed to be successful, I followed the steps exactly. Now when I visit the [https://domain.com](https://domain.com), I get a white page with just "Index of /" written in the top left corner in big bold letters. Is this a problem with the SSL or is it now simply a problem of the redirection for HTTPS traffic? It's a self-signed SSL certificate, not an officially purchased one so I get the red SSL in the address bar (Chrome) with the red line through it signifying it is an untrusted certificate. That's fine, from there I can view the details of the certificate. Is my SSL certificate working or did I do something wrong somewhere? Visiting the site without the HTTPS (just using HTTP) works fine.

In my virtual hosts file I do have all traffic forwarding to the .ca domain from this .com domain.

One of the tutorials I followed was this one:
[http://xmodulo.com/2014/04/https-apache-web-server-centos.html](http://xmodulo.com/2014/04/https-apache-web-server-centos.html)
It is also centos.

---

### Post by cj13579 on 2014-08-16
To be honest that sounds more like a virtual host problem than an SSL problem. From what you have described the SSL connection is working fine. Can you post the contents of you Virtual Host file?

---

### Post by Maheriano on 2014-08-18
> **cj13579 said:**
> To be honest that sounds more like a virtual host problem than an SSL problem. From what you have described the SSL connection is working fine. Can you post the contents of you Virtual Host file?

I left out the port 80 configuration but that's what I copied to make this one. I also left out the lines which were commented out and I replaced my domain name with the word domain.

```
<VirtualHost *:443>
        ServerName www.domain.ca
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/portal/website

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/portal/website/>
                Options FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        Alias /awstatsclasses "/usr/share/awstats/lib/"
        Alias /awstats-icon/ "/usr/share/awstats/icon/"
        Alias /awstatscss "/usr/share/doc/awstats/examples/css"

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        ScriptAlias /awstats/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog logs/dealers-ssl_error.log

        CustomLog logs/dealers-ssl_access.log combinedio

        Alias /doc/ "/usr/share/doc/"
        <Directory "/usr/share/doc/">
                Options Indexes MultiViews FollowSymLinks
                AllowOverride None
                Order deny,allow
                Deny from all
                Allow from 127.0.0.0/255.0.0.0 ::1/128
        </Directory>

        ErrorDocument 403 /common/403.php
        ErrorDocument 404 /common/404.php

        SSLEngine on

SSLCertificateFile /etc/httpd/certs/domain.com.crt
SSLCertificateKeyFile /etc/httpd/certs/domain.com.key

        SSLCertificateChainFile /etc/ssl/certs/DigiCertCA.crt

        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                SSLOptions +StdEnvVars
        </Directory>

        BrowserMatch "MSIE [2-6]" \
                nokeepalive ssl-unclean-shutdown \
                downgrade-1.0 force-response-1.0

        BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown

</VirtualHost>

```

---

### Post by Maheriano on 2014-08-18
Oops. I just saw that I have it set up for .ca and not .com. I changed the address in my browser to .ca and it worked fine. My mistake.

---

