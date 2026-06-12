---
title: "changed documentroot - now style sheet doesn't load"
date: 2009-07-10
forum: Server Platforms
---

### Post by cover3 on 2009-07-10
i changed the sites-available/default as follows and now when i try to access the site, the content loads, but the style sheet and/or template do not. (see attached screenshot)

it seems like something simple, but i can't figure out what i need to change??

> <VirtualHost *:80>
	ServerAdmin 
	
	DocumentRoot /var/www/wordpress
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /var/www/wordpress>
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

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


*UPDATE*
i also found this in the apache2 error logs
> File does not exist: /var/www/wordpress/wordpress

---

