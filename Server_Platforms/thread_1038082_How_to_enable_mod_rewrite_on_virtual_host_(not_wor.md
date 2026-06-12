---
title: "How to enable mod_rewrite on virtual host (not working?)"
date: 2009-01-12
forum: Server Platforms
---

### Post by supergrover1981 on 2009-01-12
Hi gang,

I've just set up my first Apache virtual host, but I can't seem to get mod_rewrite working. Even with nothing in htaccess except RewriteEngine On, I get an internal server error when trying to access a mod_rewrite address.

Error log tells me mod_rewrite is not installed, but strangely enough, mod rewrite works fine on /etc/apache2/sites-available/default (but not on the virtual at /etc/apache2/sites/available/websitev2)

/etc/apache2/sites/available/websitev2 attached below - any help sincerely appreciated.

```

<VirtualHost 127.0.0.2:80>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/websitev2/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/websitev2/>
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
        AllowOverride All
        Order deny,allow
        Deny from all
        Allow from 127.0.0.2/255.0.0.0 ::1/128 
    </Directory>

</VirtualHost>


```

---

### Post by spiderbatdad on 2009-01-12
So you are using an .htaccess file, and your rewrite rules are in that file?
It's been awhile since I used .htaccess, and it seems I may have used a similar technique for awhile. I have since changed to AuthType Basic Require valid user in the virtual hosts file...where I have several virtual hosts.
I do have one rewrite condition in the virtual host file it looks like this:
```
	<IfModule mod_rewrite.c>
	<IfModule mod_ssl.c>
	<Location /squirrelmail>
		RewriteEngine on
		RewriteCond %{HTTPS} !^on$ [NC]
		RewriteRule . https://%{HTTP_HOST}%{REQUEST_URI}  [L]
	</Location>
	</IfModule>
	</IfModule>

```This is contained inside <Directory></Directory> tags.

Also noticed log level is warn for this directory, maybe turning it up would produce more info? 
Of course you have enabled the site? I only ask because it seems strange that rewrite would work on one site and not the other.

---

### Post by mbeach on 2009-01-12
I'll point it out just in case its not a typo
/etc/apache2/sites/available/websitev2
should be
/etc/apache2/sites-available/websitev2

also, instead of using the .htaccess, is there a reason you are not putting it right inside your virtual host directory config?

example for a typolight installation
```

        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all

                RewriteEngine On
                RewriteBase /
                RewriteCond %{REQUEST_FILENAME} !-f
                RewriteCond %{REQUEST_FILENAME} !-d
                RewriteRule .* index.php [L]

        </Directory>

```

---

### Post by R.Bucky on 2009-01-12
I can assume that you have enabled the mod using:

```
sudo a2enmod
sudo /etc/init.d/apache2 restart
```

---

