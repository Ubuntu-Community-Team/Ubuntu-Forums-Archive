---
title: "Virtualhost help"
date: 2011-04-11
forum: Server Platforms
---

### Post by donniezazen on 2011-04-11
Hello,

I have Ajaxplorer and Ampache installed. I am tying to assign them easy domain names using dyndns but both domain names open localhost and then i can navigate to either one of the above. Can you please help me setup virtualhost so different domain resolve different locations.

```
<VirtualHost *:80>
   ServerName donniezazen.dyndns.org
   DocumentRoot /var/www/explorer
</VirtualHost>

<VirtualHost *:80>
   ServerName donniemusic.dyndns.org
   DocumentRoot /var/www/ampache
   <Directory /var/www/ampache>
      AllowOverride All
      Order allow,deny
      Allow from all
      DirectoryIndex index.html index.htm default.htm index.php default.php
   </Directory>
</VirtualHost> 

```

> sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]

Thanks.

---

### Post by rubylaser on 2011-04-11
You need to add a ServerName line to your apache2.conf like this...
```
ServerName "server_name.domain.com"
``` in order for the message to go away.

---

### Post by donniezazen on 2011-04-12
Thanks it helped solve the problem. The above virtual host file failed to resolve localhost except Ajaxplorer. So, i reverted it to original as below. But it one link opens ajaxplorer and other link just opens localhost.

Thanks.

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

<VirtualHost *:80>
   ServerName donniezazen.dyndns.org
   DocumentRoot /var/www/explorer
</VirtualHost>


<VirtualHost *:80>
   ServerName donniemusic.dyndns.org
   DocumentRoot /var/www/ampache
  </VirtualHost> 

```

---

### Post by donniezazen on 2011-04-12
I figured it out. Thanks.

---

