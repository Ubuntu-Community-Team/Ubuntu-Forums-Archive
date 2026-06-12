---
title: "Apache and Wordpress"
date: 2010-02-08
forum: Server Platforms
---

### Post by compeee2008 on 2010-02-08
I'm trying to setup my wordpress to be the main site ([http://localhost](http://localhost)) but the problem it doesn't seem to pick up my stylesheet. I have change the default file in /etc/apaches/sites-available/ to the following but the stylesheet does not work:

```
DocumentRoot /var/www/wordpress
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/wordpress/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

```

It works fine when I leave the document root and directory to /var/www but I would have to type [http://localhost/wordpress](http://localhost/wordpress) which I don't really want. Its there a setting that I am missing?

---

### Post by Puck7 on 2010-02-08
restart apache after you configured it.

---

### Post by compeee2008 on 2010-02-08
I resolve it. Stupid me, it was an internal setting in Wordpress.

---

