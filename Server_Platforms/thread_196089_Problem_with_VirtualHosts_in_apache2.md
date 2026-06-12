---
title: "Problem with VirtualHosts in apache2"
date: 2006-06-13
forum: Server Platforms
---

### Post by maciu on 2006-06-13
Hello,

I was searching throught the forum, but couldnt find a answer to my problem... One week ago i was runnig apache on breezy and everything was fine and recetely i upgraded to dapper and following that i upgraded my WWW (apache 2.0.55) server, and today i upgraded my PHP to ver 5.  and ? and my vhosts stoped to work! I have many vhosts, among them two for my main site (blog). so its all beautifull but i cant acces the site thought [http://maciu.net](http://maciu.net), while throught [www.maciu.net](www.maciu.net) it works normaly, the same applies for the rest of vhosts i have defined... any ideas ?

```
<VirtualHost *>
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/
	ServerName maciu.net
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

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
```

```
<VirtualHost *>
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/
	ServerName www.maciu.net
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

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

```

---

### Post by mushr00m on 2006-06-14
Why not use ServerAlias directive to serve both domain.tld and www.domain.net from the same vhost?

```

<VirtualHost *>
ServerName yourdomain.tld
ServerAlias www.yourdomain.tld
</VirtualHost>

```

Mushr00m

---

### Post by LordHunter317 on 2006-06-14
Yes, you should be using ServerAliases.

Anyway, your issue is probalby a hostname resolution one.  Is your DNS correct?

---

### Post by maciu on 2006-06-15
yeah i re-wrote all my vhosts using the ServerAlias directive. Now it seems to work well, only one thing that remains strange - when i try to open the site from the computer the server is running on - i still get the same result :) When i open it from [http://maciu.net](http://maciu.net), the browser attempts to download this file 
```
<?php 
/* Short and sweet */
define('WP_USE_THEMES', true);
require('./wp-blog-header.php');
?>
```

And when i open it from oher comuter both domains work normally...

---

