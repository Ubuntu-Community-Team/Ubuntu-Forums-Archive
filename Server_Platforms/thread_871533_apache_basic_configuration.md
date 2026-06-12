---
title: "apache basic configuration"
date: 2008-07-27
forum: Server Platforms
---

### Post by mfrna on 2008-07-27
Hello,

I've installed apache php mysql combination

but I would like to change the document root from /var/www to /media/DISK1_VOL3/server/Apache2/htdocs

where /media/DISK1_VOL3/ is fat32 drive

I edited the sites_available/default file to become

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /media/DISK1_VOL3/server/Apache2/htdocs/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /media/DISK1_VOL3/server/Apache2/htdocs/>
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

but now all I get from apache is the 403 forbidden error
help

---

### Post by tamoneya on 2008-07-27
This may be stating the obvious but I want to make sure we dont miss some easy fix but have you restarted apache since you editted the file.```
sudo /etc/init.d/apache2 restart
```

---

### Post by cariboo on 2008-07-27
How about if you create a symlink to the directory in /var/www eg:

```
ln -s /media/DISK1_VOL3/server/Apache2/htdocs/ htdocs
```

Just leave your doc root as /var/www

---

