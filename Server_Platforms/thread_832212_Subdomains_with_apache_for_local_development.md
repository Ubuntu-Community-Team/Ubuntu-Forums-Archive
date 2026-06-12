---
title: "Subdomains with apache for local development"
date: 2008-06-17
forum: Server Platforms
---

### Post by DaanVB on 2008-06-17
Hi there,

I just set up apache with php5, etc. I only use this server for testing my website when my free host is down again.

I'm completely new at this and simply can't figure out how to add subdomains. I can see all the files in /var/www when I enter "daan-desktop" (my PC's network name if that's the correct term) in the firefox adress bar. But I would like to add subdomains to daan-desktop (subdomain1.daan-desktop for example).

I've tried fiddling with the httpd.conf and hosts files, entered everything I could find on the web, but all I get when I restart apache is:
```
* Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```
or
```
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Tue Jun 17 21:16:51 2008] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Tue Jun 17 21:16:51 2008] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Tue Jun 17 21:16:51 2008] [warn] NameVirtualHost *:80 has no VirtualHosts
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Tue Jun 17 21:17:01 2008] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Tue Jun 17 21:17:01 2008] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Tue Jun 17 21:17:01 2008] [warn] NameVirtualHost *:80 has no VirtualHosts
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                   
```

The two applicable hosts file entries:
```
127.0.1.1 daan-desktop
127.0.2.1 sub.daan-desktop
```

Version one of the httpd.conf file:
```
# Ensure that Apache listens on port 80
Listen 80

# Listen for virtual host requests on all IP addresses
NameVirtualHost *:80

<VirtualHost *:80>
DocumentRoot /var/www/
ServerName daan-desktop

# Other directives here

</VirtualHost>

<VirtualHost *:80>
DocumentRoot /var/www/sub
ServerName sub.daan-desktop

# Other directives here

</VirtualHost> 
```

Version two of the httpd.conf file:
```
# Ensure that Apache listens on port 80
Listen 80

<VirtualHost 127.0.1.1>
DocumentRoot /var/www
ServerName daan-desktop
</VirtualHost>

<VirtualHost 127.0.2.1>
DocumentRoot /var/www/sub
ServerName sub.daan-desktop
</VirtualHost>
```

Neither works.

I would greatly appreciate any help.

---

### Post by cdenley on 2008-06-17
Post this output
```

sudo cat /etc/apache2/sites-enabled/*
sudo cat /etc/apache2/ports.conf

```

It seems you are not familiar with the modular configuration ubuntu uses for apache2.

[https://help.ubuntu.com/community/ApacheMySQLPHP#head-8c16bcd2517fa5b9fa35d616f00d3bb59e981373](https://help.ubuntu.com/community/ApacheMySQLPHP#head-8c16bcd2517fa5b9fa35d616f00d3bb59e981373)

---

### Post by DaanVB on 2008-06-17
> **cdenley said:**
> It seems you are not familiar with the modular configuration ubuntu uses for apache2.

[https://help.ubuntu.com/community/ApacheMySQLPHP#head-8c16bcd2517fa5b9fa35d616f00d3bb59e981373](https://help.ubuntu.com/community/ApacheMySQLPHP#head-8c16bcd2517fa5b9fa35d616f00d3bb59e981373)
You're right, this is my second day on ubuntu. :) And about the third day I'm trying to make sense of apache and everything webserver-related. It's been a lot easier to set everything up than I expected.

I'll take a look at that link in a moment.

And here's the output:

sudo cat /etc/apache2/sites-enabled/*
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
```
sudo cat /etc/apache2/ports.conf
```
Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>
```

---

### Post by cdenley on 2008-06-17
Your problem is probably from having two lines in your config that say "NameVirtualHost *" and two lines that say "Listen 80". You shouldn't be using httpd.conf. You should edit /etc/apache2/sites-available/default instead.

---

### Post by DaanVB on 2008-06-17
Thanks a lot! The other errors make a lot more sense now too. I was finally able to do a restart *without* any errors and *with* subdomains.

I really want to host my own website now, would be nice to have complete control over everything on the server. But the idea of hackers, having a machine on 24/7 and the bandwith usage (we still have bandwith limits in Belgium) turn me off again.

Thanks again!

---

