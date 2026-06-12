---
title: "Apache default not working in 8.10"
date: 2009-04-13
forum: Server Platforms
---

### Post by disappearedng on 2009-04-13
Hey everyone,
on my 8.10 
I have the following:

```

/etc/apache/ports.conf
NameVirtualHost *:80
Listen 80

```

and this is my default-000
```

disappearedng@disappearedng-desktop:/etc/apache2/sites-enabled$ cat 000-default <VirtualHost *:80>
    	ServerName some.domain.com
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
		DirectoryIndex index.php
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

Note that I made sure that this file is linked using a2ensite on /etc/apache/sites-enabled.

It used to work, but some it just broke. 

When i visit localhost, I am getting a blank page. And under /var/www I have an index.php that has always worked ( it's just <?php echo "Hello" ?>)


```

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Mon Apr 13 14:06:01 2009] [warn] NameVirtualHost *:80 has no VirtualHosts

```
This is the error message

thx

---

### Post by apel_2804 on 2009-04-13
Try to remove "ServerName some.domain.com" in your config file "/etc/apache2/sites-available/default". And check if php is enabled: "a2enmod php5".

---

### Post by disappearedng on 2009-04-13
nope, that didn't work

---

### Post by jms1989 on 2009-04-14
Try giving a ip address for it to listen to, for example: 127.0.0.1.

Change *:80 to 127.0.0.1:80 and reload apache to see if that works.

---

### Post by disappearedng on 2009-04-14
That worked! but only for localhost though. 

How can I make it for *?

---

### Post by Iowan on 2009-04-14
My */etc/apache2/ports.conf* contains: ```
Listen 80

<IfModule mod_ssl.c>
  Listen 443
</IfModule>
```

That "Could not reliably determine..." message -
[http://ubuntuforums.org/showpost.php?p=5678856&postcount=10]("http://ubuntuforums.org/showpost.php?p=5678856&postcount=10")

---

### Post by Kareeser on 2009-04-14
As for the php page:

You need to modify your "DirectoryIndex" line to parse php files as index files.

Also, PHP is not being loaded on your system since your server is not rendering them, but just spitting out the code. Make sure PHP is enabled, and when done, restart/reload apache.

```
sudo /etc/init.d/apache2 reload
```

---

### Post by jms1989 on 2009-04-14
> **disappearedng said:**
> How can I make it for *?

I would copy the default file to a new file like [www.mylocaldomain.com](www.mylocaldomain.com) then change the virtualhost ip to 192.168.x.x:80 (Your server's ip address) then change the directories to match your custom directory structure, the html/php dir, logs, custom docs if you need it (but you can remove that if you want, cgi-bin location, and other optional entries. Once complete, create a symlink from the sites-available dir to the sites-enabled dir.

Make sure you have set a static ip for the server or you will need to change it every time the  server's ip changes.

---

