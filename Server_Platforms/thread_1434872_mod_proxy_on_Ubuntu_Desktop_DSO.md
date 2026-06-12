---
title: "mod_proxy on Ubuntu Desktop DSO?"
date: 2010-03-20
forum: Server Platforms
---

### Post by emyr42 on 2010-03-20
As a temporary measure, my dev machine will be accessible to the outside word, with our router forwarding ports 22 and 80 to my machine.

I have a php app set up in the default virtualhost, and want to add a Grails app. The grails app runs on [http://localhost:8080/mailscan](http://localhost:8080/mailscan) and I want to configure apache2 to proxy that folder to Jetty using mod_proxy.

Module is enabled
```
$ sudo a2enmod proxy
Module proxy already enabled

```sites-available/default:
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
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

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

    ProxyRequests Off
    ProxyPreserveHost On
    <Proxy *>
        Order deny,allow
        Allow from all
    </Proxy>

    ProxyPass /mailscan http://localhost:8080/mailscan
    ProxyPassReverse /mailscan http://localhost:8080/mailscan


</VirtualHost>
```Error:
> [Sun Mar 21 00:14:56 2010] [warn] proxy: No protocol handler was valid for the URL /mailscan. If you are using a DSO version of mod_proxy, make sure the proxy submodules are included in the configuration using LoadModule.[SIZE=4]My apache2.conf contains no LoadModule lines, and a2enmod says it's already enabled. Does Ubuntu Desktop (Karmic) use the DSO versions of modules, or did I miss something else?[/SIZE]

I'm aware I should also use mod_proxy_html to make sure only the "portless" version of the address is outputted, but I can fix that later!

---

### Post by emyr42 on 2010-03-22
Enabled mod_proxy_http and it worked, but nothing I read mentioned this as an obligatory step and googling the error message isn't very helpful...

---

