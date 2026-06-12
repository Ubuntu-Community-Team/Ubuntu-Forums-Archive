---
title: "How to bind phpmyadmin to localhost only"
date: 2010-03-18
forum: Server Platforms
---

### Post by lapichiflati on 2010-03-18
Hi,

Have basic LAMP setup on 9.10 box.  I want to have a publicly accessible website AND I want to have phpmyadmin available.  The only thing is I would rather not have the phpmyadmin interface available on the internet.  I usually open a ssh port forwarded tunnel when I need to use phpmyadmin on this server.  I want to add a directive to make phpmyadmin bind only on localhost.

I have found the phpmyadmin config file in /etc/apache2/conf.d

phpmyadmin.conf -> ../../phpmyadmin/apache.conf

I have tried adding some LISTEN directives, but apache does not like my directives-- I am obviously not doing it right.  
I have looked for a bit on the internet and can't find out how to disable external access to a configured site in Apache.  Any suggestions would be welcome!

---

### Post by cdenley on 2010-03-18
I think this would work:
```

# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
	[B]Order Deny,Allow
	Deny from All
	Allow from 127.0.0.1[/B]
	Options Indexes FollowSymLinks
	DirectoryIndex index.php

	<IfModule mod_php5.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>

</Directory>

# Authorize for setup
<Directory /usr/share/phpmyadmin/setup>
    <IfModule mod_authn_file.c>
    AuthType Basic
    AuthName "phpMyAdmin Setup"
    AuthUserFile /etc/phpmyadmin/htpasswd.setup
    </IfModule>
    Require valid-user
</Directory>

# Disallow web access to directories that don't need it
<Directory /usr/share/phpmyadmin/libraries>
    Order Deny,Allow
    Deny from All
</Directory>
<Directory /usr/share/phpmyadmin/setup/lib>
    Order Deny,Allow
    Deny from All
</Directory>


```

---

### Post by lapichiflati on 2010-03-18
Yes indeedy, that works, thanks for the help.  I was actually onto the answer right when you emailed me by actually reading the apache manual.

---

### Post by harryhere on 2012-03-11
well ... i want to know that where to put this file 

that much i can guess is that it is an .htaccess file and its actual location should be phpmyadmin folder only but still.. 

to confirm because even as per the first line of the code..

Alias /phpmyadmin /usr/share/phpmyadmin

i don't have the folder "/usr/share/phpmyadmin"

although i renamed the folder "phpmyadmin" which holds the database to something else but even that name is not available..

---

