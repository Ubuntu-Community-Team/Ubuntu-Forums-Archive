---
title: "Apache Help..."
date: 2006-01-20
forum: Server Platforms
---

### Post by Phil the Geek on 2006-01-20
(Just as a quick note, sorry if this is in the wrong section. I am not running a special server install - I just ran the default one as I use this machine for other things. If this shouldn't be here, feel free to tell me and/or move it. ^_^)

I have just recently set up an apache server with PHP5 and MySQL 4.0.24 on Ubuntu 5.10. The default site, [http://localhost](http://localhost), points correctly to /var/www/. If I put a file inside that folder to run phpinfo(); everything works.

The trouble comes when I create a user specific site. The one that I am using is [http://localhost/phil/](http://localhost/phil/) which should point to /home/philip/public_html/

This works fine, however, when I try to run a phpinfo(); file from the /home/philip/public_html/ directory, I get the following:
> Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/home/philip/public_html/phpinfo.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

There is nothing in the error log about this.

The two files that I have changed are posted below.

**/etc/apache2/sites-available/default/**
> NameVirtualHost *
<VirtualHost *>
	ServerAdmin <removed for posting online>
	
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
                # Commented out for Ubuntu
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

    Alias /phil/ "/home/philip/public_html/"
    <Directory "/home/philip/public_html/">
        Options Indexes FollowSymLinks
        AllowOverride All
        Order allow,deny
        Allow from all
    </Directory>

</VirtualHost>

**/etc/apache2/conf.d/alias/**
> 
    Alias /phil/ "/home/philip/public_html/"
    <Directory "/home/philip/public_html/">
        Options Indexes FollowSymLinks
        AllowOverride All
        Order allow,deny
        Allow from all
    </Directory>


Any help would be great,

Thanks!

~Philip

---

