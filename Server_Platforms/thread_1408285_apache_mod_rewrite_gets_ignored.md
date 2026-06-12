---
title: "apache mod_rewrite gets ignored"
date: 2010-02-16
forum: Server Platforms
---

### Post by mandavi on 2010-02-16
Hey,

my rewrite-rule gets simply ignored and I can't find the mistake...

I activated the module by 'sudo a2enmod rewrite' and 'apache2ctl -M' returns among others the line:

```
 rewrite_module (shared)
```


My 000-default in sites-enabled contains:
```

DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride **All**
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride **All**
		Order allow,deny
		allow from all
	</Directory>
```


the httpd.conf contains:

```
 RewriteEngine on
    RewriteRule ^/book/(.*)$ /b/index.php?title=$1 
```



Also a .htaccess with the same content of httpd.conf exists in localhost/.htaccess.

But when I request [http://localhost/book/anything](http://localhost/book/anything) I only get a 404 for /book/anything.
Any idea what else I could check?

Thanks for help!

---

### Post by cdenley on 2010-02-16
Did you restart apache so it can load the rewrite module (as the a2enmod command's output you to)? I'm not sure why the .htaccess wouldn't work, but I don't think your default vhost will inherit global options created in httpd.conf. In fact, httpd.conf should not be used for anything, I believe. Put your rewrite rules in the vhost configuration, then
```

sudo /etc/init.d/apache2 restart
echo -e "GET /book/anything HTTP/1.0\n"|nc 127.0.0.1 80

```

---

### Post by mandavi on 2010-02-16
Moving the rules to vhost did the trick - thanks a lot. It should be possible to add it to a directory-container inside of httpd.conf too though. What disturbs me a little is, that the .htaccess files was ignored - do I need to activate the file somehow?

---

### Post by cdenley on 2010-02-16
> **mandavi said:**
> Moving the rules to vhost did the trick - thanks a lot. It should be possible to add it to a directory-container inside of httpd.conf too though. What disturbs me a little is, that the .htaccess files was ignored - do I need to activate the file somehow?

I don't think so. Check the permissions, but I think if the file exists but is unreadable by www-data, it will give you a 500 error.
```

ls -l /var/www/.htaccess

```

See if you can use the file to restrict access.
```

order deny,allow
deny from all

```

---

### Post by mandavi on 2010-02-16
I've changed file permissions and a 'ls -l /var/www/.htaccess' returns:
```
-rw-rw-rw- 1 www-data www-data 74 2010-02-15 23:52 /var/www/.htaccess

```

Still after restarting apache I get the 404. The log-files don't contain anything beside the 'does not exist - 404'

---

