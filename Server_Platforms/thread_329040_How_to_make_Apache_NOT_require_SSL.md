---
title: "How to make Apache NOT require SSL?"
date: 2006-12-31
forum: Server Platforms
---

### Post by mcmanus on 2006-12-31
Hey y'all,

I just installed a 6.06.1 Dapper server install on a box, and I have Apache2 + SSL working fine, except now the problem is I can't access my site WITHOUT SSL...  d'oh!

Does anyone know how to enable SSL for a virtual hosted site without requiring it?  Here is my /etc/apache2/sites-available/default file:

```

<VirtualHost *>
        ServerAdmin admin@mydomain.com
        ServerName www.mydomain.com
        ServerAlias mydomain.com *.mydomain.com
        DocumentRoot /var/www/www.mydomain.com
        SSLEngine on
        #SSLOptions +StdEnvVars
        SSLCertificateFile /etc/ssl/certs/wwwcert.pem
        SSLCertificateKeyFile /etc/ssl/private/wwwcert--keyunsecured.pem
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/www.mydomain.com>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

---

### Post by evilghost on 2006-12-31
```

luser@VMHOST:/etc/apache2/sites-enabled$ cat 000-packetmail

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /home/e-smith/files/ibays/primary/html
        ServerName www.mydomain.com
        ServerAlias mydomain.com

        <Directory /home/e-smith/files/ibays/primary/html>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature Off
</VirtualHost>

<VirtualHost *:443>
        SSLEngine On
        SSLCertificateFile /etc/apache2/ssl/apache.pem

        ServerAdmin webmaster@localhost
        DocumentRoot /home/e-smith/files/ibays/primary/html
        ServerName www.mydomain.com
        ServerAlias mydomain.com

        <Directory /home/e-smith/files/ibays/primary/html>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature Off
</VirtualHost>

```

---

### Post by mcmanus on 2007-01-01
Wow, thanks!  That worked!



](*,)

---

