---
title: "Forcing apache to redirect HTTP traffic to HTTPS"
date: 2008-05-11
forum: Server Platforms
---

### Post by kdepa on 2008-05-11
I have been trying to figure out how to get Apache to automatically switch to https whenever someone visits my website through unsecured http.  I have tried using the rewrite engine, but each time i always get the message > Your browser sent a request that this server could not understand.
Reason: You're speaking plain HTTP to an SSL-enabled server port.
Instead use the HTTPS scheme to access this URL, please.  Below I have my /etc/apache2/sites-enabled/default information.  What am I doing wrong here?

> NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        SSLEngine on
        SSLOptions +StrictRequire
        SSLCertificateFile /etc/ssl/certs/server.crt
        SSLCertificateKeyFile /etc/ssl/private/server.key
        RewriteEngine On
        RewriteCond %{HTTPS} off
        RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
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


---

### Post by mojo90 on 2008-05-11
Try this
```
<VirtualHost 192.168.0.100:80>
    ServerName  example.com/
    Redirect / https://example.com/
</VirtualHost>

<VirtualHost 192.168.0.100:443>
        ServerName example.com
        DocumentRoot /var/www/

        SSLEngine on
        SSLCertificateFile /etc/apache2/server.crt
        SSLCertificateKeyFile /etc/apache2/server.key
</VirtualHost>

```

---

### Post by kdepa on 2008-05-11
It works! Thank you so much.  I ended up having to tweak a couple of other things in the file to make it work.

What I did:
> 
defaultNameVirtualHost [www.qirfa.com:80](www.qirfa.com:80)
<VirtualHost www.qirfa.com:80>
        Servername [www.qirfa.com/](www.qirfa.com/)
        Redirect / [https://www.qirfa.com/](https://www.qirfa.com/)
</VirtualHost>
NameVirtualHost [www.qirfa.com:443](www.qirfa.com:443)
<VirtualHost www.qirfa.com:443>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        SSLEngine on
        SSLOptions +StrictRequire
        SSLCertificateFile /etc/ssl/certs/server.crt
        SSLCertificateKeyFile /etc/ssl/private/server.key
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                Order allow,deny
                allow from all

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

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


---

### Post by ethernet on 2008-11-30
Had issues getting redirection to work but changing the domain name to *:80 and *:443 worked:

```

<VirtualHost *:80>
    ServerName  me.dyndns.biz/
    Redirect / https://me.dyndns.biz/
</VirtualHost>

<VirtualHost *:443>
        ServerName me.dyndns.biz
        DocumentRoot /var/www/

        SSLEngine on
        SSLCertificateFile /etc/apache2/server.crt
        SSLCertificateKeyFile /etc/apache2/server.key
</VirtualHost>

```

Hope this helps someone. Don't forget to
```
/etc/init.d/apache reload
```
after altering the files in sites-available :KS

---

### Post by us3rQUE on 2011-11-17
Perfect thanks!

---

### Post by chandan_raka on 2012-10-11
I tried almost all options given in the virtual host style. 

ServerName wiki.my.net
    RedirectMatch (.*) https://wiki.my.net$1

And -----------


ServerName wiki.my.net
    Redirect / [https://wiki.my.net](https://wiki.my.net)

And -----

ServerName wiki.my.net
    Redirect permanent / [https://wiki.my.net](https://wiki.my.net)

However, whenever I check my apache access logs, it never shows it is actually redirecting to the "https" link

---

### Post by CharlesA on 2012-10-11
This thread is about 4 year old, if you are having problems, I suggest you create a new thread on the subject.

---

