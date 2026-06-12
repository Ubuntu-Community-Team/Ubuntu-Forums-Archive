---
title: "RewriteMap not allowed here - in Virtual Host ?"
date: 2010-03-04
forum: Server Platforms
---

### Post by ZeeZeer on 2010-03-04
When I reload apache I get an error:
"RewriteMap not allowed here"

Document Root folder location:
/var/www/car

Virtual host location:
/etc/apache2/sites-enabled/car

Contained inside the 'car' file 
```


<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName www.car.com
    DocumentRoot /var/www/car
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>

    <Directory /var/www/car>

        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
        
        RewriteEngine On
        RewriteBase /
        RewriteMap insensitive tolower:
        RewriteRule ^[\/]*(.*)$ /${insensitive:$1} [R,L]

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


```

I'm running just a basic Xubuntu 9.10 server. mod_rewrite is enabled and working. But I'm not sure what I'm missing to make urls map to lowercase. Why am I getting this error?

---

### Post by cdenley on 2010-03-04
[http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html#rewritemap](http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html#rewritemap)

You cannot define a rewriting map within a directory tag. It only supports a global or vhost context, not a directory context.

---

### Post by ZeeZeer on 2010-03-06
Thanks cdenley. I know I still have a lot to learn. 

I moved the rewrite code out of the <Directory> tags and into just the <VirtualHost> tags and it worked. Also, instead using the rewrite code in my original post I used the code below instead. 
  
  RewriteEngine On
  RewriteMap  lc int:tolower
  RewriteCond %{REQUEST_URI} [A-Z]
  RewriteRule (.*) ${lc:$1} [R=301,L]

The new 'car' file inside /etc/apache2/sites-enabled/ is below. I hope this thread can help some people.

```


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

