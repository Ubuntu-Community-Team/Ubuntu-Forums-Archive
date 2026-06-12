---
title: "[SOLVED] Apache2 &amp;amp; mod_ssl?"
date: 2008-10-20
forum: Server Platforms
---

### Post by angstsix on 2008-10-20
hello,
I'm trying to enable ssl on my ubuntu apache2 server.

right now if I try to enable it I get this error:
Invalid command 'SSLEngine', perhaps misspelled or defined by a module not included in the server configuration

ok, so I figured that i don't have it installed. so I try to run:

#apt-get install libapache-mod-ssl

which returns this:

Package libapache-mod-ssl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache-mod-ssl has no installation candidate

hoping that someone here knows how to do this as I'm a little stuck at the moment.:confused:

thanks in advance for your time!
-Ken

---

### Post by cdenley on 2008-10-20
The module is included in the apache2.2-common package. I believe it is a dependecy of the mpm and prefork packages, so you already have it installed. To enable it:
```

sudo a2enmod ssl

```
My vhost configuration looks something like
```

NameVirtualHost *:443
<VirtualHost *:443>
        ServerName www.mydomain.com
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/
        SSLEngine on
        SSLOptions +FakeBasicAuth -StrictRequire +ExportCertData
        SSLCertificateFile /etc/ssl/certs/mycert.crt
        SSLCertificateKeyFile /etc/ssl/private/www.key
        SSLCertificateChainFile /etc/ssl/certs/gd_intermediate_bundle.crt
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride AuthConfig Options FileInfo Limit
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

```
Of course, this is in addition to the default vhost which listens on port 80. You will need to provide apache an SSL certificate.

---

### Post by angstsix on 2008-10-20
yup, your right, it was there;
module ssl_module is already loaded, skipping

the only thing that i was missing was: NameVirtualHost *:443

aw I'm such a n00b!

thanks for your help!!!

---

