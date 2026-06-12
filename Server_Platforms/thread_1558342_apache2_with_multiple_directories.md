---
title: "apache2 with multiple directories"
date: 2010-08-22
forum: Server Platforms
---

### Post by Thyagaraj on 2010-08-22
Apache2 default directory is /var/ww. Is it possible to add one more directory(/usr/share/tomcat/webapps) to apache config.? so that i can have both /var/www as well as /usr/share/tomcat/webapps

Thank you all!

---

### Post by Lars Noodén on 2010-08-23
Yes.  There are several ways to do that.  One is to make use of the runtime directives, [directory](http://httpd.apache.org/docs/2.3/mod/core.html#directory) and, maybe, [alias](http://httpd.apache.org/docs/2.3/mod/mod_alias.html#alias).

---

### Post by Thyagaraj on 2010-08-27
Please any one show me how to do this without any errors..

---

### Post by rubylaser on 2010-08-27
I just use vhosts.  

Create a file in /etc/apache2/sites-available for each subdomain you'd like to host and then enable those domains.

This is a very simple example for hostname website and would be located at /etc/apache2/sites-available/website

```
<VirtualHost *:80>
    ServerName www.domain.com
    DocumentRoot /var/www/website/public/
</VirtualHost>
```

This is an SSL site located at /etc/apache2/sites-available/ecommerce

```
<Virtualhost *:443>
        ServerName ecommerce.domain.com
        SSLEngine On
        SSLCertificateFile /etc/apache2/ssl/ecommerce.domain.com.crt
        SSLCertificateKeyFile /etc/apache2/ssl/ecommerce.domain.com.key
        DocumentRoot /var/www/ecommerce/public/
</Virtualhost>
```

I like to add this to the bottom of my /etc/apache2/apache2.conf file so that traffic gets compressed and I set expires headers...

```
# GZIP files
AddOutputFilterByType DEFLATE text/html text/css text/plain text/xml application/x-javascript
BrowserMatch ^Mozilla/4 gzip-only-text/html
BrowserMatch ^Mozilla/4\.0[678] no-gzip
BrowserMatch \bMSIE <img src="no-gzip" alt="" />gzip-only-text/html

# Expire Headers
ExpiresActive On
ExpiresDefault "access plus 10 years"
```

To enable a website just type...
```
a2ensite website
```

or
```
a2ensite ecommerce
```

Then, restart apache
```
/etc/init.d/apache2 restart
```


Doing this, you can add many different directories to host websites (although, I'd recommend putting all your created apps in /var/www, that's the default).

Just make sure they are owned by www-data with the correct permissions...

```
chown -R www-data:www-data /var/www
chmod -R 755 /var/www
```

Hope that helps.

---

