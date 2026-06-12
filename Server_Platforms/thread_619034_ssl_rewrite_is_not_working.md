---
title: "ssl rewrite is not working"
date: 2007-11-21
forum: Server Platforms
---

### Post by winstonzeng on 2007-11-21
my ssl rewrite was working before but now it stopped working. i dont know how to solve this.
here is my sites-avaliable default.

NameVirtualHost *:80
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	RewriteEngine   on
	RewriteCond     %{SERVER_PORT} ^80$
	RewriteRule     ^/webmail(.*)$ https://%{SERVER_NAME}/webmail$1 [L,R]
	RewriteLog      "/var/log/apache2/rewrite.log"
	RewriteLogLevel 2	

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

### Post by MrFSL on 2007-11-21
I use something similar to this on my servers:

> # Force redirect to https
    RewriteEngine On
    RewriteCond %{HTTPS} !=on
    RewriteRule ^/(.*) https://%{SERVER_NAME}%{REQUEST_URI} [R]


---

### Post by winstonzeng on 2007-11-21
ill give this a try. thanks


EDIT: still doesn't work..

EDIT: omg, i feel so stupid. i forgot to restart apache2. everything is working flawlessly. thanks MrFSL

---

### Post by MrFSL on 2007-11-21
No problem. 
:)

---

