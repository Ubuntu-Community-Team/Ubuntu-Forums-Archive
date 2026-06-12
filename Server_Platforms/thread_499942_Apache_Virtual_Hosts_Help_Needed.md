---
title: "Apache Virtual Hosts Help Needed"
date: 2007-07-13
forum: Server Platforms
---

### Post by medw1974 on 2007-07-13
I'm not sure if what I'm trying to achieve is actually possible but here goes ....

I'm setting up a development server on a dual boot XP and Ubuntu 7.04 machine and would like to have a common webroot shared between both os'es. So I have created a FAT32 partition (sda4) and created a var/www directory on this partition.

The virtual hosts I want to add are as follows:

```
# localhost
<VirtualHost *>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www
    ServerName localhost
    ErrorLog logs/localhost-error_log
    CustomLog logs/localhost_access_log common
</VirtualHost>

# Galleon
<VirtualHost *>
    ServerAdmin webmaster@localhost
    DocumentRoot /media/sda4/var/www/galleon
    ServerName galleon
    ErrorLog logs/galleon-error_log
    CustomLog logs/galleon-access_log common
    Alias /CFIDE /var/www/CFIDE
</VirtualHost>
```

My original apache2.conf doesn't have the usual section 3 relating to virtual hosts but instead has this:

```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
```

This is the contents of the file that gets included:

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
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

</VirtualHost>
```

I have tried adding my virtual hosts to the end of this file as well as commenting out the include line on apache2.conf and adding them in there but both times apache wont start giving the following error:

```
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [fail]

```

Any ideas on how to get this to work?

---

### Post by Mr. C. on 2007-07-13
Dont use "localhost" as your virtual server's name.  Consider what happens when you are on host X and type :

[http://localhost](http://localhost)

Which host will the browser attempt to connect to?  Answer: host X, not your server.  Localhost is a special name, and is always used to mean the local machine, which of course, is relative.

MrC

---

### Post by gregor171 on 2007-07-16
I'm not sure what you'd like to acchieve, but if you have a domain name, you have to create VirualHost:

```
# Galleon
NameVirtualHost yourdomainname.com

<VirtualHost *>
    ServerAdmin webmaster@localhost
    ServerName localhost
	ServerName www.yourdomainname.com
	ServerAlias yourdomainname.com *.yourdomainname.com #for http://yourdomainname.com
	DocumentRoot /media/sda4/var/www/galleon
    ErrorLog logs/localhost-error_log
    CustomLog logs/localhost_access_log common
</VirtualHost>

```

* you need this only if you have  **[www.yourdomainname.com](www.yourdomainname.com)**, if not create Virtual hosts.

if you'd like to create virual host -->  **[http://your-ip/galleon](http://your-ip/galleon)** , you have to create alias. Create filenamed **galleon**  in:

```

/etc/apache2/sites-available

```

Put this code for your shared disc:
```

# http://your-ip/galleon
Alias /galleon /media/sda4/var/www/galleon
		
<Directory /media/sda4/var/www/galleon>
	Options Indexes FollowSymLinks
	AllowOverride All
	Order allow,deny
	Allow from all
</Directory>



```

and run:

```
a2ensite galleon
```

Reastart Apache!

---

