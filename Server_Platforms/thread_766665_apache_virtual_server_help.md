---
title: "apache virtual server help"
date: 2008-04-25
forum: Server Platforms
---

### Post by MattBA on 2008-04-25
Could someone help me out with this, I am new at this so I must be overlooking one bit of detail. 

Here's my problem, I have installed a Wordpress blog in the /var/www/ directory which I can access perfectly from [http://localhost/wordpress/](http://localhost/wordpress/) 
but when I set up my virtual host so that the default website [http://localhost/](http://localhost/) points to the Wordpress blog all I get is a website with just text and no theme. Why would that happen? 

I followed these instructions to set up my virtual host [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Here is what my "/etc/apache2/sites-available/mysite" file looks like:

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/wordpress/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/wordpress/>
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

---

### Post by terazen on 2008-04-25
Hey, This is a stab in the dark, but in your wordpress configuration does it have a setting for what it thinks itself is?  Possibly apache has it at [www.domain.com](www.domain.com) and wordpress sees itself at [www.domain.com/wordpress?](www.domain.com/wordpress?)

The themes stuff is under /var/www/wordpress/wp-content/themes/ so if apache starts with /var/www/wordpress/ then all should work.  I'd focus on the wordpress settings.  Good luck.

---

