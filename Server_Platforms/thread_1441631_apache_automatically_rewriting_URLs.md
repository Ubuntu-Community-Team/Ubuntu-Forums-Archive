---
title: "apache automatically rewriting URLs?"
date: 2010-03-29
forum: Server Platforms
---

### Post by svargo on 2010-03-29
So I have a really weird problem. I enabled mod_rewrite using a2enmod, but now apache automatically rewrites pages (like it's inheriting). For example, any page with a .php extension can be accessed with or without the extension. For example, example.com/page.php = example.com/page = example.com/page/! There are NO .htaccess files on the server anywhere! I did a full sudo search. Is there something in the apache configuration that automatically does this. I've never seen it before. I need to write custom rewrites, and this is screwing everything up.

Please help!

---

### Post by Ryan Dwyer on 2010-03-29
The configuration that causes this doesn't need to be in a .htaccess file. It could be in any *.conf file in /etc/apache2/.

Also note .htaccess files are hidden and might not appear in your search results. ls -a will show hidden files.

---

### Post by cdenley on 2010-03-29
[http://httpd.apache.org/docs/2.2/content-negotiation.html#negotiation](http://httpd.apache.org/docs/2.2/content-negotiation.html#negotiation)
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks **[COLOR="Red"]MultiViews[/COLOR]**
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

