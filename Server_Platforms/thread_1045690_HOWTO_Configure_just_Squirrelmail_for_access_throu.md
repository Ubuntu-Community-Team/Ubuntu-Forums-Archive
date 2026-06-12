---
title: "HOWTO Configure just Squirrelmail for access through HTTPS"
date: 2009-01-20
forum: Server Platforms
---

### Post by cirobr on 2009-01-20
Hello,

I need to configure Apache2 on my Ubuntu Hardy Server so that my main page (let´s say [www.example.com](www.example.com)) is accessed through HTTP, and Squirrelmail ([www.example.com/squirrelmail](www.example.com/squirrelmail)) through HTTPS. Further details are given below:

[LIST]
[*]Standard installation of both Apache2 and Squirrelmail gives regular access for both pages through HTTP.
[*]By configuring file /etc/apache2/sites-available/default for HTTPS as described at the end of the article found [here]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html"), makes both pages to be accessed through HTTPS.
[*]On the file /etc/apache2/sites-available/squirrelmail, there is a standard configuration that supposedly would give HTTPS access just to Squirrelmail, when uncommented. After doing so, Apache could not be reloaded.
[/LIST]

Any help on finding a solution is greatly appreciated.

Thanks.

---

### Post by spiderbatdad on 2009-01-20
In the virtual hosts file put the squirrel mail site first.
It must have its own FQDN, in other words, you must have at 
least two sites registered and of course listen on 443.
List your other FQDN in it own container listen on 80
Also create a separate directory for the squirrel mail files...not in the same document root as your other site.
Alias the site in /etc/hosts like so:
<local ip address> example1.com example2.com

restart the server.


Example of a vitual host container I used for squirrelmail

```
<VirtualHost *:443>
	ServerAdmin my@email.com
	ServerName my.fqdn.org
	DocumentRoot /www/squirrelmail/
		SSLEngine On
	 <Directory /www/squirrelmail>
                Options FollowSymLinks MultiViews
                AllowOverride none
                Order allow,deny
                allow from all
        </Directory>

	<Directory /usr/share/squirrelmail>
		Options Indexes FollowSymLinks
	<IfModule mod_php4.c>
		php_flag register_globals off
	</IfModule>
	<IfModule mod_php5.c>
		php_flag register_globals off
	</IfModule>
	<IfModule mod_dir.c>
		DirectoryIndex index.php
	</IfModule>

  # access to configtest is limited by default to prevent information leak
#	<Files configtest.php>
#		order deny,allow
#		deny from all
#		allow from 127.0.0.1
#	</Files>
	</Directory>

		ErrorLog /var/log/apache2/error-webmail.log 
 
		CustomLog /var/log/apache2/access-webmail.log combined 

# redirect to https when available (thanks omen@descolada.dartmouth.edu)

	<IfModule mod_rewrite.c>
	<IfModule mod_ssl.c>
	<Location /squirrelmail>
		RewriteEngine on
		RewriteCond %{HTTPS} !^on$ [NC]
		RewriteRule . https://%{HTTP_HOST}%{REQUEST_URI}  [L]
	</Location>
	</IfModule>
	</IfModule>

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel info

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

---

### Post by cirobr on 2009-01-22
Thanks! It worked with slight changes for my server.

---

