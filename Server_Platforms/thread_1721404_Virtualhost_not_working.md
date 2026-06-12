---
title: "Virtualhost not working"
date: 2011-04-04
forum: Server Platforms
---

### Post by Doulos1 on 2011-04-04
I have several virtual hosts set up.  All of them work fine except one.  They all are supposed to be identical except for the domain specific info.  The one that doesn't work is accessible via 192.168.1.8:8080/~name . I changed the pertinent info but here it is:  

```
<VirtualHost 192.168.1.8:8080>
    ServerName mydomain.com
    ServerAdmin myemail@gmail.com
    ServerAlias www.mydomain.com
    DocumentRoot /home/name/public_html
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /home/name/public_html/>
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

    CustomLog /var/log/apache2/name/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

``` When I try to access this domain with [http://mydomain.com](http://mydomain.com) it takes me to my router login screen. Anyone see anything wrong that I am missing, or know why this is happening?

---

### Post by Kljuka on 2011-04-04
Is the server listening on port 8080. Normally it uses only port 80.
Is the config file OK (what does ```
apache2ctl configtest
``` say?)

Are you using ISPconfig? If yes, then you should also check ownership and permissions of directory. And ISPconfig configuration (available from web).

---

### Post by Doulos1 on 2011-04-04
As to 8080, yes.  I set it up that way to reduce the traffic since I use it only sparingly from the outside. This server is in my house.

I'll have to get back to you on the other.

---

### Post by Doulos1 on 2011-04-05
status: OK

For some reason I am being taken to my server root instead of the virtual host:

[http://mydomain.com/](http://mydomain.com/) takes me to router admin
[http://mydomain.com/~username](http://mydomain.com/~username) takes me to virtual host

[http://otherdomain.com/](http://otherdomain.com/) takes me to that domain via virtual host as expected

](*,)

---

