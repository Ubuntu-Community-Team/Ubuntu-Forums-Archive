---
title: "LAMP permissions problem"
date: 2007-07-12
forum: Server Platforms
---

### Post by mokojin on 2007-07-12
hi

I'm using ubuntu 7.04 desktop, and I'm trying to put a folder on my home dir to be accessible for apache, to use as a PHP develpment environment. But when I try to use it I have permisson denied. where's my config:

```

<VirtualHost *>
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

	Alias /fmarques /home/ricardo/workspace/fmarques_web/
	<Directory "/home/ricardo/workspace/fmarques_web">
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/docc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

My directory is /home/ricardo/workspace/fmarques_web/

the permissions on that dir are:

```

-rwxrwxrwx 1 www-data ricardo  332 2007-07-11 20:44 application.php
drwxrwxrwx 4 www-data ricardo 4096 2007-07-11 20:58 APP_PRIVATE
-rwxrwxrwx 1 www-data ricardo 3390 2007-07-07 10:50 content.php
drwxrwxrwx 3 www-data ricardo 4096 2007-07-07 10:50 extra
drwxrwxrwx 2 www-data ricardo 4096 2007-07-07 10:50 images
drwxrwxrwx 2 www-data ricardo 4096 2007-07-11 20:29 includes
-rwxrwxrwx 1 www-data ricardo   52 2007-07-11 20:43 index.php
drwxrwxrwx 2 www-data ricardo 4096 2007-07-07 10:50 style
drwxrwxrwx 3 www-data ricardo 4096 2007-07-11 21:04 template
-rwxrwxrwx 1 www-data ricardo 1095 2007-07-07 10:50 user.php

```

thanks in advance

---

### Post by simonn on 2007-07-12
www-data probably does not have permissions to /home/ricardo/. It is probably not a good idea to give www-data permissions to your home dir either!

Possibly a better way of doing this is:

```

$ sudo mkdir /var/www/fmarques
$ sudo chown ricardo:www-data /var/www/fmarques
$ sudo chmod 660 /var/www/fmarques
$ ln -s /var/www/fmarques /home/ricardo/workspace/fmarques_web

```

You will need to add yourself to the www-group.

Hope this makes sense?

---

