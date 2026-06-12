---
title: "LAMP with localhost subdomains"
date: 2011-07-22
forum: Server Platforms
---

### Post by gurnarok on 2011-07-22
Hi, I was trying to create localhost server with subdomains, but it doesn't seem to work.

I was following [this guide]("https://help.ubuntu.com/community/LocalhostSubdomain"). I did all the required steps, but it doesn't work after 2 subdomains, a.localhost worked, but after adding b.localhost it stopped from working, it just redirects to a.localhost

What could be the problem?

Here are some config files that I have edited, by the guidance of the previously mentioned link.

```

root@Grimoire:~# cat /etc/hosts
127.0.0.1 a.localhost
127.0.0.1 b.localhost
127.0.1.1 Grimoire
root@Grimoire:~# cat /etc/apache2/sites-available/a 
<VirtualHost *>
	DocumentRoot /var/www/a/
	ServerName a.localhost

	<Directory /var/www/a/>
		Options Indexes FollowSymLinks MultiViews
		#AllowOverride None
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>
	ErrorLog /var/log/apache2/a-error.log
	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/a-access.log combined
</VirtualHost>
root@Grimoire:~# cat /etc/apache2/sites-available/b
<VirtualHost *>
	DocumentRoot /var/www/b/
	ServerName b.localhost

	<Directory /var/www/b/>
		Options Indexes FollowSymLinks MultiViews
		#AllowOverride None
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>
	ErrorLog /var/log/apache2/b-error.log
	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/b-access.log combined
</VirtualHost>

```

Hope these might be able to help.

---

### Post by volkswagner on 2011-07-22
I'm not sure why it is not mentioned in the tutorial, buy apache needs to "know" you want to use the NameVirtualHost directive.

Try adding the following to
/etc/apache2/httpd.conf

```
NameVirtualHost *
```

I have seen your symptom many many times.  Seems some folks never got it to work.  I have yet to find in any documentation where this directive should actually reside.  I have seen posts recommending placing the above line in ports.conf.  So you could try each location if one or the other does not work.

Be sure to restart apache after the change.

---

### Post by gurnarok on 2011-07-22
Great! Now it works as it should work. Should try to get someone update the page with up-to-date info.

Update: Added the info that volkswagner gave into the community help page. Hope it helps other people too.

---

