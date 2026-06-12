---
title: "Trying to get Apache2 to point to correct virtual host directory"
date: 2007-09-03
forum: Server Platforms
---

### Post by flyinggreg on 2007-09-03
I got my web site almost fully running.  I am using Apache2 and have a couple virtual hosts: 1) localhost, 2) sql-ledger, and 3) my web site.

I can look at sql-ledger just fine on my localhost, and got my web site forwarded so I can see it off the LAN.  Now, the problem I am having is pointing the virtual host for the web site at the correct directory on the host machine.  Every time I enter the web site name into a browser (on or off the LAN), I don't get the web site default.html.  Instead I get my root directory.  I've tried several times modifying the DocumentRoot directive several times in my /etc/apache2/sites-available/default to point to the correct directory.  Here's a snapshot of the file.  I need some help figuring out what needs to change to correctly display the web site directory /var/www/Web_Server  

Thanks!

```
NameVirtualHost wingandrotors.com
<VirtualHost www.wingandrotors.com>
	DocumentRoot /var/www/Web_Server	
	<Directory />
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
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
	ServerSignature Off

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

