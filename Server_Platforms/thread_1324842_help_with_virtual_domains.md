---
title: "help with virtual domains"
date: 2009-11-12
forum: Server Platforms
---

### Post by kylegio on 2009-11-12
story of my life recently, things that were working have stopped working. 
i need to host two websites from my server and only have one domain name, lets say my domain name is example.com, this domain works great, it gets its documents from /var/www/  now lets say i want to have sub.example.com and it get its documents from /var/sub

i cant seem to do this, it was working and then after a restart it doesnt work along with a bunch of other stuff. now sub.example.com just points to /var/www documents as well. the sites are not related and its upsetting for people who are trying to access one sight to be accessing something completely different.

i have probably messed up my site configuration files but this is what i have now
default file
```

NameVirtualHost example.com:80
<VirtualHost *:80>
	ServerName example.com
	DocumentRoot /var/www/
</VirtualHost>

<VirtualHost example.com:80>
	ServerAdmin webmaster@localhost
	ServerName example.com
	ServerAlias www.example.com
	DocumentRoot /var/www/
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
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

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

sub file:
```

<VirtualHost sub.example.com:80>
ServerName example.com
ServerAdmin webmaster@localhost
ServerAlias www.example.com
DocumentRoot /var/sub
#we want specific log file for this server
ErrorLog /var/log/apache2/sub-error.log
CustomLog /var/log/apache2/sub-access.log combined
</VirtualHost>


```

where along the way have i gone completely wrong, all i really need to do is have a subdomain pointing at a completely different document root then anything else, so for example [www.example.com](www.example.com) or example.com go to /var/www while sub.example.com looks for documents in /var/sub.

can anyone set me straight? thanks!

---

### Post by kevin11951 on 2009-11-12
> **kylegio said:**
> story of my life recently, things that were working have stopped working. 
i need to host two websites from my server and only have one domain name, lets say my domain name is example.com, this domain works great, it gets its documents from /var/www/  now lets say i want to have sub.example.com and it get its documents from /var/sub

i cant seem to do this, it was working and then after a restart it doesnt work along with a bunch of other stuff. now sub.example.com just points to /var/www documents as well. the sites are not related and its upsetting for people who are trying to access one sight to be accessing something completely different.

i have probably messed up my site configuration files but this is what i have now
default file
```

NameVirtualHost example.com:80
<VirtualHost *:80>
	ServerName example.com
	DocumentRoot /var/www/
</VirtualHost>

<VirtualHost example.com:80>
	ServerAdmin webmaster@localhost
	ServerName example.com
	ServerAlias www.example.com
	DocumentRoot /var/www/
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
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

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

sub file:
```

<VirtualHost sub.example.com:80>
ServerName example.com
ServerAdmin webmaster@localhost
ServerAlias www.example.com
DocumentRoot /var/sub
#we want specific log file for this server
ErrorLog /var/log/apache2/sub-error.log
CustomLog /var/log/apache2/sub-access.log combined
</VirtualHost>


```

where along the way have i gone completely wrong, all i really need to do is have a subdomain pointing at a completely different document root then anything else, so for example [www.example.com](www.example.com) or example.com go to /var/www while sub.example.com looks for documents in /var/sub.

can anyone set me straight? thanks!

remove the ":80" from everything you posted...  trust me.  Theres more you have to do, but do that and let me know what happens.

---

### Post by Ilalmi on 2009-11-13
Your site configuration files seem ok. Although I wouldn't use the same values in ServerName and ServerAlias of both sites, if the sites aren't related. But that isn't the problem.
Are you sure, your sub configuration file is read and used by the server? 
Does your server write anything into the sub log files? 
What's the bunch of other stuff you mentioned that doesn't work any more?

---

### Post by kylegio on 2009-11-13
EDIT: See post below i think i found a working solution, the following was posted before solution :/EDIT


> **kevin11951 said:**
> remove the ":80" from everything you posted...  trust me.  Theres more you have to do, but do that and let me know what happens.

here is my new config files
```

NameVirtualHost example.com
NameVirtualHost *
Listen 80
<VirtualHost *>
        ServerName example.com
        DocumentRoot /var/www/
</VirtualHost>

<VirtualHost example.com>
        ServerAdmin webmaster@localhost
        ServerName example.com
        ServerAlias example.com
        DocumentRoot /var/www/
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
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks


```
```

<VirtualHost sub.example.com>
ServerName example.com
ServerAdmin webmaster@localhost
ServerAlias www.sub.example.com
DocumentRoot /var/sub/
#we want specific log file for this server
ErrorLog /var/log/apache2/sub-error.log
CustomLog /var/log/apache2/sub-access.log combined
</VirtualHost>

```

all error/access logs are created, however the only logs taht ever seem to be written to are error.log which after hitting the webserver a couple times with a normal browser looks like this
(ps i added the x's to obscure the ip i connected to the server with)
```
[Fri Nov 13 11:59:40 2009] [notice] Apache/2.2.12 (Ubuntu) DAV/2 SVN/1.6.5 PHP/5.2.10-2ubuntu6.1 with Suhosin-Patch mod_ssl/2.2.12 OpenSSL/0.9.8g configured -- resuming normal operations
[Fri Nov 13 12:02:44 2009] [error] [client xx.xxx.xx.xxx] File does not exist: /var/www/favicon.ico
[Fri Nov 13 12:02:44 2009] [error] [client xx.xxx.xx.xxx] File does not exist: /var/www/favicon.ico
[Fri Nov 13 12:03:00 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:01 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:02 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:03 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:04 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:05 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:06 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:07 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:08 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:09 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:10 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:11 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:12 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:13 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:14 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:15 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:16 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:17 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:18 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:19 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Fri Nov 13 12:03:20 2009] [warn] (101)Network is unreachable: connect to listener on [::]:80

```
before accessing the webserver only the first line saying resuming normal operations is there, the others happen when i actauly connect to it with a web browser.

the only other log to be written to is other_vhost_access.log, the access.log and the sub-access.log are not written to.. they used to be but are not now. it appears to me that everything is getting caught by that * virtual host. no matter what i do i get files from the * virtual hosts document root

follow up:
this is in fact the case, i have changed the DocumentRoot for VirtualHost * and everything now points to that document root, its like my other VirtualHost do not matter :( i have also tried commenting out the NameVirtualHost * and the VirtualHost * (all of it) and the server is now un-reachable, just gives a "The requested URL / was not found on this server." page im assuming because now theres no documentroot for anything?

---

### Post by kylegio on 2009-11-13
i think i have a working solution, have to do some more testing but basically:
example.com, [www.example.com](www.example.com) -> /var/www
sub.example.com ->/var/sub

here are my files
```

NameVirtualHost *
Listen 80
<VirtualHost *>
	ServerAdmin webmaster@localhost
	ServerName example.com
	ServerAlias www.example.com
	DocumentRoot /var/www/
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
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

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


and the other
```
<VirtualHost *>
ServerName sub.example.com
ServerAdmin webmaster@localhost
ServerAlias www.sub.example.com
DocumentRoot /var/www/sub/
ErrorLog /var/log/apache2/sub-error.log
CustomLog /var/log/apache2/sub-access.log combined
</VirtualHost>

```


how does that look to people?

---

