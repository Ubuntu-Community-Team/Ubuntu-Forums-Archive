---
title: "Apache virtual host (again...)"
date: 2009-10-16
forum: Server Platforms
---

### Post by atakacs on 2009-10-16
Probably an easy one but I'm pretty new to Ubuntu / Debian - please bear with me... ;)

I have found other forum posts with similar problems but as far as I can tell nothing relevant to that specific problem.

I am trying to setup a very plain vanilla static web site on an Ubuntu 8.04 server.

I have the system loaded with Apache 2 and the default web site works.
I have made sure the [www.mynewsite.com]("http://www.mynewsite.com") resolves to that machine.
I have copied my html files into /var/www/mynewsite
I have created an entry in /etc/apache2/sites-available for mynewsite which reads

```
<VirtualHost *>
      ServerAdmin webmaster@localhost
      ServerName  www.mynewsite.com      
      ServerAlias   mynewsite.com  
      
      DocumentRoot /var/www/mynewsite
      
      <Directory /var/www/mynewsite>
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

      # Possible values include: debug, info, notice, warn, error, crit,
      # alert, emerg.
      LogLevel info
      ErrorLog /var/log/apache2/mynewsite.error.log
      CustomLog /var/log/apache2/mynewsite.access.log combined

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
```I have run /usr/sbin/a2ensite with success for mynewsite
I have reloaded apache by issuing "/etc/init.d/apache2 reload" without any error reported.

Unfortunately my site doesn't load - just hangs...

I have tried (localy) 

apache2ctl -S

which results in

```
VirtualHost configuration:
wildcard NameVirtualHosts and _default_ servers:
*:*                    is a NameVirtualHost
         default server localhost (/etc/apache2/sites-enabled/000-default:2)
         port * namevhost localhost (/etc/apache2/sites-enabled/000-default:2)
         port * namevhost www.mynewsite.com (/etc/apache2/sites-enabled/mynewsite:1)
Syntax OK
```which seems ok to my untrained eyes...

also tried 

wget [http://www.newsite.com](http://www.newsite.com)

resulting in 

```
--14:36:42--  http://www.newsite.com/
           => `index.html'
Resolving www.newsite.com... xxx.xxx.48.49
Connecting to www.newsite.com|xxx.xxx.48.49|:80... failed: Connection timed out.
Retrying.

--14:39:57--  http://www.newsite.com/
  (try: 2) => `index.html'
Resolving www.newsite.com... xxx.xxx.48.49
Connecting to www.newsite.com|xxx.xxx.48.49|:80... failed: Connection timed out.
```The domain specific logs are created but remain empty...
The generic apache log doesn't contain anything relevant as far as I tell...

What piece am I missing ?!

Thanks in advance for any suggestion / pointer

Regards

alex

---

### Post by Lars Noodén on 2009-10-18
Alex,

There can only be one default.  Also, the name-based virtual host listed in /etc/apache2/ports.conf may be port-specific.

Try something like  [FONT="Courier New"]<VirtualHost  xxx.xxx.48.49:80>[/FONT]

---

### Post by atakacs on 2009-10-19
Thanks for your help.

I modified the   [FONT=Courier New]<VirtualHost> directive as per you suggestion to no avail.[/FONT]
It seems that the connection to [www.newsite.com|xx.xx.48.49|:80](www.newsite.com|xx.xx.48.49|:80)... does not get through (i.e. the request is routed correctly but there is no listener at the other end, although default site on port 80 works just fine...

Nothing relevant in the logs...

btw /etc/apache2/ports.conf is empty on my Ubuntu 8.04 / Apache 2 setup

Regards

alex

---

### Post by Lars Noodén on 2009-10-20
> **atakacs said:**
> 
btw /etc/apache2/ports.conf is empty on my Ubuntu 8.04 / Apache 2 setup



Look around to see if there are any Listen directives, we don't want to contradict them.

[INDENT][FONT="Courier New"]grep -r Listen /etc/apache2/*.conf[/FONT][/INDENT]

Make a backup copy of ports.conf

[INDENT][FONT="Courier New"]sudo cp /etc/apache2/ports.conf  /etc/apache2/ports.conf.orig[/FONT][/INDENT]

And then make sure these lines are there in ports.conf:

NameVirtualHost *:80
Listen 80

That would be my next guess.

---

### Post by atakacs on 2009-10-20
Hi

Thanks for your help

I eventually managed to pinpoint a networking issue before the http request actually managed to reach the server !

It's all fine now !

Regards

alex

---

