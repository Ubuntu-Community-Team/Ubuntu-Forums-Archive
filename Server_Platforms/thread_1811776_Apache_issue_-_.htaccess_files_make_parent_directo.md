---
title: "Apache issue - .htaccess files make parent directories disappear"
date: 2011-07-25
forum: Server Platforms
---

### Post by micahharwell on 2011-07-25
Running Ubuntu Server 11.04
Apache 2.2.17

When I browse my webserver, autoindexing shows all the files, but only directories that do not have an .htaccess file.

For example, let's say I have directory containing four directories named "commingsoon", "current", "draft", and "misc".

If I browse there, this is what I see:

```
Index of /genericwebsite
   comingsoon/     20-Dec-2010 07:54
   current/        25-May-2008 21:33
   draft/          26-Jan-2011 06:25
Apache/2.2.17 (Ubuntu) Server at 192.168.1.10 Port 80
```

The only difference is that "misc" contains an .htaccess file. If I manually type in //myserver/genericwebsite/misc I get

> Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.

Apache/2.2.17 (Ubuntu) Server at 192.168.1.10 Port 80

An empty .htaccess file does not make this problem happen. But the following simple .htaccess files will:

```
<Files .htaccess>
order allow,deny
deny from all
</Files>
```

```
<FilesMatch "\.(html|shtml|htm|php)$">
Header set Cache-Control "max-age=3600, proxy-revalidate"
</FilesMatch>
```

```
Redirect permanent /index.shtml			http://www.website.com/index.php
```

Now I can solve this by setting AllowOverride None in the Apache configuration file, but of course then I am not able to use .htaccess files - and I would like to be able to use them.

Here is a copy of my Apache configuration file:
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	AddType	text/html	.shtml
	AddOutputFilter INCLUDES .shtml
	DirectoryIndex index.html index.php index.shtml
	ServerName glue

	DocumentRoot /srv/data1/data/web/online
	<Directory />
		Options FollowSymLinks Includes Indexes
		AllowOverride All
		Allow from all
		Order deny,allow
		AuthType Basic
		AuthName "Micah's web server"
		AuthUserFile /srv/data1/data/web/.htpasswd
		Require valid-user
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel crit

	CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
```

Any help would be appreciated. Thank you.

---

