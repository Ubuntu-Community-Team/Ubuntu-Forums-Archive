---
title: "Virtual host - domain 2 showing wrong"
date: 2008-06-04
forum: Server Platforms
---

### Post by eddie67 on 2008-06-04
[www.domain.com](www.domain.com) is showing OK, located in /var/www/ directory

[www.anotherdomain.com](www.anotherdomain.com) which is located in /var/www/anotherdomain.com/ is showing with correct URL, but with the same content as in [www.domain.com](www.domain.com) 

Anyone know where I should look?

Thanks

Eddie.

---

### Post by quelx on 2008-06-04
Do you have a **ServerName** directive for *[www.anotherdomain.com](www.anotherdomain.com)*?  There will be much guessing unless you can post your the config files in **/etc/init.d/sites-enabled** and perhaps some logs.

---

### Post by eddie67 on 2008-06-05
Thanks.

Here are my files:

**Default:**

NameVirtualHost *:80
<VirtualHost *>
	ServerAdmin [email]myname@gmail.com[/email]
	
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
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
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


**firstdomain.com.conf**

<VirtualHost domain.com>
ServerAdmin [email]post@domain.com[/email]
ServerName domain.com
ServerAlias [www.domain.com](www.domain.com)
DocumentRoot /var/www/
CustomLog /var/log/apache2/firstdomain.com.log combined
</VirtualHost>


**anotherddomain.com**

<VirtualHost anotherddomain.com>
ServerAdmin [email]post@anotherddomain.com[/email]
ServerName anotherddomain.com
ServerAlias *.anotherddomain.com
DocumentRoot /var/www/anotherddomain.com/
CustomLog /var/log/apache2/anotherddomain.com.log combined
</VirtualHost>


Thanks.

Eddie.

---

### Post by quelx on 2008-06-05
The **VirtualHost** directive tells apache to listen on an address not the name os the server, so that needs to be changed to ***:80** (any address at port 80).  Nothing else jumps out at me.  For future convenience make sure the two files are in **/etc/apache2/sites-enabled** and run ```
sudo a2ensite firstdomain.com.conf
sudo a2ensite anotherdomain.com
sudo /etc/init.d/apache2 reload
```

*/etc/apache2/sites-avaliable/firstdomain.com.conf*
```
<VirtualHost [COLOR="Red"]*:80[/COLOR]>
ServerAdmin post@domain.com
ServerName domain.com
ServerAlias www.domain.com
DocumentRoot /var/www/
CustomLog /var/log/apache2/firstdomain.com.log combined
</VirtualHost>
```

*/etc/apache2/sites-avaliable/anotherddomain.com*
```
<VirtualHost [COLOR="Red"]*:80[/COLOR]>
ServerAdmin post@anotherddomain.com
ServerName anotherddomain.com
ServerAlias *.anotherddomain.com
DocumentRoot /var/www/anotherddomain.com/
CustomLog /var/log/apache2/anotherddomain.com.log combined
</VirtualHost>
```

You may find this helpful.
[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)

Let us know how it goes.

---

