---
title: "Smokeping accesseable from Apache2"
date: 2007-08-03
forum: Server Platforms
---

### Post by MatsB on 2007-08-03
Hi,

I need some basic help with SmokePing. I've installed Apache2, rrdtool, SpeedyCGI, smokeping on a newly installed Ubuntu 7.0.4 laptop.

I've been trying to follow the documentation on installing Smokeping but i'm stuck at a permission problem when i moved the smokeping.cgi file from /usr/lib/cgi-bin/ to /var/www/smokeping i get 403 forbidden You don't have permission to access /cgi-bin/ on this server. when i browse to [http://localhost/cgi-bin/](http://localhost/cgi-bin/)
Changing the ownership to www-data doesn't help.

I've also tried to change this in server@admin-laptop:/etc/apache2/sites-available/default

ScriptAlias /cgi-bin/ /var/www/cgi-bin/
<Directory "/var/www/cgi-bin">
AllowOverride None
Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
Order allow,deny
Allow from all
</Directory>


server@admin-laptop:/var/www$
drwxr-xr-x 2 root root 4096 2007-08-03 12:14 apache2-default
drwxr-xr-x 2 root root 4096 2007-08-03 12:54 cgi-bin
drwxr-xr-x 2 www-data www-data 4096 2007-03-19 22:57 smokeping

server@admin-laptop:/var/www/cgi-bin$
-rwxr-xr-x 1 root root 2362 2007-08-03 12:28 smokeping.cgi

---

### Post by slide_o_mix on 2007-08-20
I was having similar issues with it, but this is what I did to get it up and running.

You need to NOT move smokeping.cgi into /var/www/smokeping, just use the [http://localhost/cgi-bin/smokeping.cgi](http://localhost/cgi-bin/smokeping.cgi) URL instead. You also need to go into apache2.conf and find the AddHandler cgi-bin .cgi and uncomment it. That was all I had to do to get it up and running.

---

