---
title: "apache - 2 virtual hosts - very simple, cant get it working"
date: 2007-12-14
forum: Server Platforms
---

### Post by vendejp on 2007-12-14
Hello, this is very frustrating... i simply want port 80 to point to:
/var/www/

and another port (lets say 8000) to point to:
/var/www/test

i copied the /etc/apache2/sites-available/default config and simply changed the "80" to "8000" as well as the DocumentRoot and Directory to the subdirectory.  Imagine the file below with these few changes in the second config.

then a "a2ensite test"
then a restart.  port 80 works, but nothing on 8000, its like the servers down.

Anyone have any suggestions?  Ive scoured these posts for a similar problem and have tried lots of small tweaks from other similar issues with virtual hosts, but its all a no go.

Thanks in advance

```


NameVirtualHost *:80
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
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

```

---

### Post by ebash on 2007-12-14
You have to tell apache to listen on the 8000. This is done by adding the directive to you configuration file.

```
Listen 8000
```

You can add this directive at the beginning of your site's configuration file or in the file /etc/apache2/ports.conf.

---

### Post by vendejp on 2007-12-14
perfect.  That worked.  Thanks!

---

