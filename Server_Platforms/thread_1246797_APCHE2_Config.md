---
title: "APCHE2 Config"
date: 2009-08-22
forum: Server Platforms
---

### Post by martynbristow on 2009-08-22
Hi
I'm new to Linux and have previously just battled with windows
I have an old PC running as an Ubuntu server. It has Apache2 installed and im having probles using the: Virtual Hosts Set Up
I have set the 'hosts' files on my other computers to send all traffic from:
server.myweb
mscweb.myweb
server
mscweb
myweb
all to the servers address port 192.168.1.10
which all works fine these addresses give me no errors however
all these addresss always resolve to the same website

```
<VirtualHost mscweb:80>
ServerAdmin mscweb@myweb
ServerName mscweb.myweb
ServerAlias mscweb
DocumentRoot /var/www/mscweb.myweb

<Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

        <Directory /var/www/mscweb.myweb>
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
                ErrorLog /var/log/apache2/avh-error.log
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
``````
<VirtualHost *:80>
ServerName server.myweb
serverAlias myweb
ServerAlias server
DocumentRoot /var/www
<Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

        <Directory /var/www>
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
</VirtualHost>

```MSCWEB is supposed to pass the /var/www/mscweb folder only
and any request to any other address shud pass /var/www but esspecially server.myweb
i have been tweaking this alot and to no joy
if i remove the enabling link it makes it work
but when i put the mscweb one bak ti becomes global again
This has been tried on ubuntu text only server, ubuntu & kubuntui tooo
please help :)

---

### Post by windependence on 2009-08-22
Configuration is not what you think on Ubuntu. Try this:

[http://beginlinux.com/server_training/web-server/994-ubuntu-804-named-based-hosting](http://beginlinux.com/server_training/web-server/994-ubuntu-804-named-based-hosting)

-Tim

---

