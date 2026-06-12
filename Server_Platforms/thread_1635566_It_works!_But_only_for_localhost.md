---
title: "It works! But only for localhost"
date: 2010-12-02
forum: Server Platforms
---

### Post by Innigo on 2010-12-02
Hi Folks,

I've been working through some instructions for setting up mod_wsgi and the first step is to get a "hello world" app working. That's been done and I've configured apache2 in what I think is the recommended default. From the same machine if I browse to 127.0.0.1 I get the Apache "It Works" page and at 127.0.0.1/myapp I get "hello world" Yay. But if I try from another machine in my organisation's network, the connections times out. It's my understanding the network does not block this kind of activity. I can ping my server by ip address from the other machine.  It's like it's not listening to anything execept localhost.

---

### Post by Innigo on 2010-12-02
Here are my config files. This is, I believe how you're supposed to do it in Ubuntu:
apache2.conf is untouched
httpd.conf is empty

ports.conf
```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
ServerName *:80
Listen *:80 


<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>
```sites-available/default contains my <Virtual Host>
```
<VirtualHost *:80>
    ServerName www.server01.my.org.com
    ServerAlias server01.my.org.com 
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www

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
        AddHandler wsgi-script .wsgi
        Order allow,deny
        Allow from all
    </Directory>
    
    WSGIScriptAlias /myapp /usr/local/pythonenv/myapp/myapp.wsgi
    
    <Directory /usr/local/pythonenv/myapp>
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

</VirtualHost>
```

---

### Post by Innigo on 2010-12-02
Got it :-) My default Apache config was correct. I just didn't know about UFW. My own local firewall was blocking all traffic as ufw was enabled but had no rules added, it must default to "deny from all"

```
$ sudo ufw allow Apache   #fixed the problem or you could go:
$ sudo ufw allow 80  
```

---

