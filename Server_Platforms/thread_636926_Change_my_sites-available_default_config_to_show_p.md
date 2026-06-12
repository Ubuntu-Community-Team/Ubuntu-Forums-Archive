---
title: "Change my sites-available default config to show php files first, and not html"
date: 2007-12-10
forum: Server Platforms
---

### Post by btwong on 2007-12-10
this should be easy, but i cannot for the life of me work this out.

I have setup all my sites on my server, but i am having trouble changing the order in which apache loads default pages. Right now it is loading the index.html file, but instead i want it to load the index.php page instead.

BUt i want it load in order, so if no index.php file is found, then go onto load the index.html file.

i know its in the sites-available/default config file, but i am not sure where to enter it.

my config file looks like this:

> NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /media/Media/wamp/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /media/Media/wamp/www/>
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

can someone please show me where to add the page order in?

thanks

---

### Post by MJN on 2007-12-10
It is the [DIrectoryIndex](http://httpd.apache.org/docs/2.0/mod/mod_dir.html#directoryindex) directive you're after.

You will have one listed in /etc/apache2/apache2.conf which applies server-wide hence if you edit that one (note the local-url order is important - it is in descending matching order) it will take effect for all your sites.

If you just want to change it for a particular virtual host then put it within your VirtualHost container (e.g. below your ServerAdmin line in your config), however if you only want it to take effect for particular directories then put it in the appropriate DIrectory container.

Mathew

---

### Post by btwong on 2007-12-11
thanks mate.

---

