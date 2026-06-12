---
title: "mod_rewrite and AllowOverride All breaks site"
date: 2009-03-06
forum: Security
---

### Post by dpcamp on 2009-03-06
I'm trying to get mod_rewrite working on my server. And when I change AllowOverride None to all it breaks my site (well at least php functionality)

Anyone know why?

here is my 000-default configuration:```
NameVirtualHost *
<VirtualHost *>
	ServerName localhost
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/htdocs/
	<Directory /var/www/htdocs/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride all
		Order allow,deny
		allow from all
		
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>
	ScriptAlias /cgi-bin/ /var/www/cgi-bin/
	<Directory "/var/www/cgi-bin">
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
	
	<Directory /var/www/htdocs/apps>
		Options Indexes FollowSymLinks MultiViews +Includes
		AllowOverride None
		Order allow,deny
		Allow from all
		SetHandler mono
		DirectoryIndex index.aspx index.html index.shtml
		AddType text/html .shtml
		AddOutputFilter INCLUDES .shtml
	</Directory>
	Alias /apps "/var/www/htdocs/apps"
	AddMonoApplications apps "/apps:/var/www/htdocs/apps"
	<location /apps>
	SetHandler mono
	</location>
	
</VirtualHost>







```

maybe this has to do with my .htaccess file?
```

ErrorDocument 404 http://www.mydomain.com/error/404.php

php_value auto_prepend_file /localfilepath/global_prepend.php

php_value auto_append_file /localfilepath/global_append.php


```
This is giving me the following error:
Warning: Unknown: failed to open stream: No such file or directory in Unknown on line 0

Fatal error: Unknown: Failed opening required '/localfilepath/global_prepend.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

---

### Post by bodhi.zazen on 2009-03-06
Moved to server platforms.

---

### Post by dpcamp on 2009-04-27
still getting this error... Anyone?

---

### Post by dpcamp on 2009-04-27
so it was the .htaccess file. I don't remember why i have the global_prepend.php file called. Got rid of it and it fixed my issue.

---

### Post by vikto on 2009-04-30
Hi, I have similar problem, I cant figure out. I set up vhost and enablend mod_rewrite. My site works fine, but when I try to access rewriterule  ^samename/([0-9]*)$  samename.php?num=$1 [L], it doesnt read the num var. When trying to change the samename.php -> xsamename.php it works fine though. I have clean synaptec install on LAMP and so far, I havent messed up settings. I am trying unsuccessfully to find out, what causes this, but no result so far. If anyone knows how to help, the beer's on me.

---

