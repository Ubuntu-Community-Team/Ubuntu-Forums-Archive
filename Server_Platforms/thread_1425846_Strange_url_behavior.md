---
title: "Strange url behavior"
date: 2010-03-09
forum: Server Platforms
---

### Post by ZeeZeer on 2010-03-09
Two virtual hosts enabled and working through a Actiontec router dynamicDNS / zoneedit setup.

I want to apply certain mod_rewrite rules to both virtual hosts. Mainly remove www from the url and rewritemap to lowercase. Under /etc/apache2/sites-enabled there are two files, domainONE and domainTWO. Currently I am just applying these rewrite rules to each sites file, but is there a way to put the code into just one file (maybe httpd.conf) and have it applied to both sites?   

Basically I'm encountering some strange behavior that I'm trying to solve.
[http://domainONE.com](http://domainONE.com) - works
[http://domainTWO.com](http://domainTWO.com) - takes me to domainONE's index.html file, but [http://domainTWO.com](http://domainTWO.com) shows in the address bar

Any and all suggestions are welcome - I'm still new to linux and apache. Thanks :)

/etc/apache2/sites-enabled/domainONE
```

<VirtualHost *:80>
    ServerAdmin my@emailaddress.com
    ServerName www.domainone.com
    DocumentRoot /var/www/domainone
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /var/www/domainone/>

        Options -Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all

  RewriteEngine On
  RewriteCond %{HTTP_HOST} ^www.domainone.com$ [NC]
  RewriteRule ^(.*)$ http://domainone.com/$1 [R=301,L]


    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride All
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
  RewriteEngine On
  RewriteMap  lc int:tolower
  RewriteCond %{REQUEST_URI} [A-Z]
  RewriteRule (.*) ${lc:$1} [R=301,L]
</VirtualHost>


```

/etc/apache2/sites-enabled/domainTWO
```

<VirtualHost *:80>
    ServerAdmin my@emailaddress.com
    ServerName www.domaintwo.com
    DocumentRoot /var/www/domaintwo
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /var/www/domaintwo/>

        Options -Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all

  RewriteEngine On
  RewriteCond %{HTTP_HOST} ^www.domaintwo.com$ [NC]
  RewriteRule ^(.*)$ http://domaintwo.com/$1 [R=301,L]


    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride All
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
  RewriteEngine On
  RewriteMap  lc int:tolower
  RewriteCond %{REQUEST_URI} [A-Z]
  RewriteRule (.*) ${lc:$1} [R=301,L]
</VirtualHost>

```

---

### Post by cdenley on 2010-03-09
Well, you have not defined a vhost for domaintwo.com, only [www.domaintwo.com](www.domaintwo.com), so the default vhost (first alphabetically) will be used.
```

<VirtualHost *:80>
    ServerAdmin my@emailaddress.com
    ServerName www.domaintwo.com
    **[COLOR="Red"]ServerAlias domaintwo.com[/COLOR]**
    DocumentRoot /var/www/domaintwo
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /var/www/domaintwo/>

        Options -Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all

  RewriteEngine On
  RewriteCond %{HTTP_HOST} ^www.domaintwo.com$ [NC]
  RewriteRule ^(.*)$ http://domaintwo.com/$1 [R=301,L]


    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride All
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
  RewriteEngine On
  RewriteMap  lc int:tolower
  RewriteCond %{REQUEST_URI} [A-Z]
  RewriteRule (.*) ${lc:$1} [R=301,L]
</VirtualHost>

```
[http://httpd.apache.org/docs/2.2/mod/core.html#serveralias](http://httpd.apache.org/docs/2.2/mod/core.html#serveralias)

---

### Post by ZeeZeer on 2010-03-09
Thank you cdenley! I made the change and it worked perfectly :)

---

