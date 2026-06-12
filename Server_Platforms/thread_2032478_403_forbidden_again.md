---
title: "403 forbidden again"
date: 2012-07-24
forum: Server Platforms
---

### Post by alenis on 2012-07-24
After one of the last updates (ubuntu 12.04), I cannot access my webpages on my computer anymore. Everytime I try, I get a 
```
Forbidden

You don't have permission to access / on this server.
Apache/2.2.22 (Ubuntu) Server at localhost Port 80
```

I checked the solutions proposed in previuos threads about the same issue to no avail.

My default file in sites-available looks like:

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/alenis/Documents/www
	<Directory />
		Options Indexes FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/alenis/Documents/www/>
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

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

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

I didn't change anything in the default configuration.

File permissions are set as, e.g.:

```

-rw-r--r--  1 www-data www-data    177 lug 23 17:58 index.html
drwxrwxrwx  2 www-data www-data   4096 nov 24  2008 javascript

```


Please help!

---

