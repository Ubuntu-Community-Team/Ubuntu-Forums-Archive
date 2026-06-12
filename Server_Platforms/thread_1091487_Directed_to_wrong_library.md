---
title: "Directed to wrong library"
date: 2009-03-09
forum: Server Platforms
---

### Post by Anders B on 2009-03-09
I had to reinstall linux on a new hd, since the old one was breaking down :(

Since that, I havent been able to acces my testforum (yyyy.isa-geek.org, same IP ofc). As you can see the two forums are both in the library Offentligt, but if i try the URL [http://yyyy.isa-geek.org](http://yyyy.isa-geek.org), I still get directed to  /home/anders/Offentligt/hollyforum/.

My httpd.conf :

```
<VirtualHost *>
ServerName xxxx.servegame.org
DocumentRoot /home/anders/Offentligt/hollyforum/
</VirtualHost>

<VirtualHost *>
ServerName yyyy.isa-geek.org
DocumentRoot /home/anders/Offentligt/testforum/
</VirtualHost>
```


Edit: Using Apache2 btw

---

### Post by cdenley on 2009-03-09
You shouldn't be using httpd.conf. Delete the configurations from it. Your site configurations should go in individual files in the directory /etc/apache2/sites-available, then enabled with the "a2ensite" command. Start by configuring your default site at /etc/apache2/sites-available/default.

---

### Post by wirelessmonkey on 2009-03-09
try with 
```

<VirtualHost *:80>
ServerName xxxx.servegame.org
DocumentRoot /home/anders/Offentligt/hollyforum/
</VirtualHost>

<VirtualHost *:80>
ServerName yyyy.isa-geek.org
DocumentRoot /home/anders/Offentligt/testforum/
</VirtualHost>

```

---

### Post by Anders B on 2009-03-10
None of those suggestions worked :(

But looking at the offcial apachesite I found this

> Some operating systems and network equipment implement bandwidth management techniques that cannot differentiate between hosts unless they are on separate IP addresses.

---

### Post by cdenley on 2009-03-10
You restarted apache, right?
```

sudo /etc/init.d/apache2 restart

```

Post this output
```

cat /etc/apache2/sites-enabled/*

```

---

### Post by Anders B on 2009-03-11
> **cdenley said:**
> You restarted apache, right?
```

sudo /etc/init.d/apache2 restart

```

Post this output
```

cat /etc/apache2/sites-enabled/*

```

Here's what I got from the **cat /etc/apache2/sites-enabled/***
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/anders/Offentligt/hollyforum
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/anders/Offentligt/hollyforum>
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
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/anders/Offentligt/hollyforum/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/anders/Offentligt/hollyforum/>
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
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/anders/Offentligt/testforum/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/anders/Offentligt/testforum/>
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
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/anders/Offentligt/testforum/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/anders/Offentligt/testforum/>
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
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/anders/Offentligt/testforum
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/anders/Offentligt/testforum>
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

### Post by cdenley on 2009-03-11
I don't see any ServerName directives in that configuration. How are you expecting apache to distinguish between virtualhosts?

---

### Post by Anders B on 2009-03-11
This is what it looks like now. Still doesnt work tho.


```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	
	ServerName xxxx.servegame.org
	DocumentRoot /home/anders/Offentligt/hollyforum/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/anders/Offentligt/hollyforum/>
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
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/anders/Offentligt/hollyforum/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/anders/Offentligt/hollyforum/>
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
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/anders/Offentligt/testforum/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/anders/Offentligt/testforum/>
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
	ServerAdmin webmaster@localhost
	
	ServerName yyyy.isa-geek.org
	DocumentRoot /home/anders/Offentligt/testforum/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/anders/Offentligt/testforum/>
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

### Post by cdenley on 2009-03-11
In what way is it not working? Any hostname except baktest.isa-geek.org would be directed to your default vhost, the first one in the configuration. All the other vhosts are missing the ServerName directive, so no hostname will result in the use of those vhosts.

Assuming your hostname is configured correctly, and you restarted apache, this link will show you your last vhost.
[http://baktest.isa-geek.org/](http://baktest.isa-geek.org/)

Any other link, such as:
[http://holly.servegame.org/](http://holly.servegame.org/)
[http://[server](http://[server) ip]/
will show your first (default) vhost.

---

### Post by Anders B on 2009-03-11
LOL.. I have no idea what has happened. 2 hours ago it didnt work, and now it does :o

Thx mate :D

---

