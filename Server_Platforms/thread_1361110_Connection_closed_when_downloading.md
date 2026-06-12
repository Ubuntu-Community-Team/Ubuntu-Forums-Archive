---
title: "Connection closed when downloading"
date: 2009-12-21
forum: Server Platforms
---

### Post by Al_Capino on 2009-12-21
I hope somebody can help me, because I can't find the solution.

I'm using ubuntu 9.04 server with apache 2.2
My webserver is on a network share.

My problem is that when I'm downloading a file from the apache site using the "wget" command, I constantly get a message that the connection is closed. It keeps downloading, but in small parts at the time.

This is also with images I have on the website, the are shown about 15%.

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /media/Storage/WWW
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /media/Storage/WWW/>
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
```

---

