---
title: "CGI outputs text of cgi file rather than running script"
date: 2008-10-22
forum: Server Platforms
---

### Post by kpm on 2008-10-22
Can anyone help me sort out why CGI scripts are not running?  

I have installed bugzilla (manually - not with apt-get) but when I navigate to the site location in the browser, the actual text of index.cgi displays rather than the rendered bugzilla home page.  I enabled the site and edited the Apache site config file like so:
```
NameVirtualHost bugs
<VirtualHost bugs>
	ServerAdmin admin@example.com
	DocumentRoot /var/www/bugs
	<Directory /var/www/bugs>
		Options Indexes FollowSymLinks ExecCGI
		AllowOverride All
		Order allow,deny
		Allow from all
	</Directory>
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>
	ErrorLog /var/log/apache2/bugs-error.log
	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn
	CustomLog /var/log/apache2/bugs-access.log combined
	ServerSignature On
</VirtualHost>
```
What am I doing wrong??
Thanks

---

### Post by lykwydchykyn on 2008-10-22
Is index.cgi in /usr/lib/cgi-bin and is it executable?

---

### Post by kpm on 2008-10-23
> **lykwydchykyn said:**
> Is index.cgi in /usr/lib/cgi-bin and is it executable?

Hmmm... nope.  So, I tried moving the entire bugzilla directory to /usr/lib/cgi-bin/. Still no luck.  I then tried pointing the ScriptAlias at the /var/www/bugzilla directory, but that didn't work either... then, after much to much fiddling about discovered that if I simply removed the whole ScriptAlias section in the sites enabled bugzilla host config file and add  "AddHandler cgi-script .cgi" then the site rendered properly.  The default site is not enabled, so apache seems to be rendering the cgi scripts with simply:
```
NameVirtualHost bugzilla
<VirtualHost bugzilla>
	ServerAdmin admin@abcdefg.com	
	DocumentRoot /var/www/bugzilla
	<Directory /var/www/bugzilla>
		AddHandler cgi-script .cgi
		Options Indexes FollowSymLinks ExecCGI
		AllowOverride All
		Order allow,deny
		Allow from all
	</Directory>
	ErrorLog /var/log/apache2/bugzilla-error.log
	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn
	CustomLog /var/log/apache2/bugzilla-access.log combined
	ServerSignature On
</VirtualHost>
```

Thanks

---

