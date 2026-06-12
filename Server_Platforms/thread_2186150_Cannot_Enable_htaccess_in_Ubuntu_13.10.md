---
title: "Cannot Enable htaccess in Ubuntu 13.10"
date: 2013-11-06
forum: Server Platforms
---

### Post by dannymichel on 2013-11-06
No matter what i do.
```
<VirtualHost *:80>
	ServerAdmin snipped
	ServerName dev.dmichel.net
	ServerAlias dev.dmichel.net
	DocumentRoot /home/danny/public_html
	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /home/danny/public_html/>
		Options Indexes FollowSymLinks
		AllowOverride All
		Require all granted
	</Directory>
</VirtualHost>
```

---

### Post by SeijiSensei on 2013-11-06
In general, if you have full control over the server you should not need any .htaccess controls.  The .htaccess method is designed to enable ISPs to grant their customers some control over their websites.  If you are responsible for the entire server, it's better to place the directives that would have been in .htaccess into the appropriate <Directory> stanzas in the virtual host configuration.

That said, I don't know why adding "AllowOverrride All" is not sufficient to enable .htaccess.  What does the error.log say?

---

### Post by dannymichel on 2013-11-06
> [Wed Nov 06 16:39:19.882384 2013] [mpm_prefork:notice] [pid 25219] AH00163: Apache/2.4.6 (Ubuntu) PHP/5.5.3-1ubuntu2 configured -- resuming normal operations
[Wed Nov 06 16:39:19.882459 2013] [core:notice] [pid 25219] AH00094: Command line: '/usr/sbin/apache2'
That's all i get in the error log

---

### Post by koenn on 2013-11-06
How do you know it's not working ?

---

### Post by dannymichel on 2013-11-06
because my custom permalinks in wordpress arent working.

---

### Post by koenn on 2013-11-06
> **dannymichel said:**
> because my custom permalinks in wordpress arent working.

i don't know wordpress, so just to have an idea:
what's in the .htaccess files that would allow permalinks  to work ?

---

### Post by dannymichel on 2013-11-06
```

# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /testsite/
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /ellementos/index.php [L]
</IfModule>

# END WordPress

```

---

### Post by koenn on 2013-11-06
and you have mod_rewrite enabled ?

---

### Post by dannymichel on 2013-11-06
oh my god, im an idiot! forgot mod_rewrite.

---

### Post by koenn on 2013-11-06
:-)

---

