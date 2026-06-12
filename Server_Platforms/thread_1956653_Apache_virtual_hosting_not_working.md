---
title: "Apache virtual hosting not working"
date: 2012-04-11
forum: Server Platforms
---

### Post by kkruecke on 2012-04-11
II have two websites I want to run. However, the content for the first site is displaying for both sites. have VPS running Ubuntu. Here is what I did:

```
# sudo aptitude install apache2 php5
# sudo cd /etc/apache2/sites-available/
# sudo cp default kurttest
# sudo cp default krueckeberg
```
I edited kurttest and krueckeberg to look like what is shown below
```
# sudo a2dissite default
# sudo a2ensite kurttest
# sudo a2ensite krueckeberg
# sudo /etc/init.d/apache2 restart

```
kurttest has
```
<VirtualHost *:80>

	DocumentRoot "/var/www/kurttest.com"
# I'm not sure what this <Directory /> is for?
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory "/var/www/kurttest.com/">
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

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
krueckeberg has 
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www/krueckeberg.org
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/krueckeberg.org>
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

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

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

### Post by SeijiSensei on 2012-04-11
If you want to use "name-based virtual hosting" each site's configuration has to have a "ServerName" directive.  Apache uses that to match the name given in the URL.  You'll also have to be able to resolve those names either with a DNS server or by static entries in the client's /etc/hosts file.

Read this: [http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)

---

### Post by kkruecke on 2012-04-11
Thanks for the prompt reply. Yes, I forgot ServerName and ServerAlias. It is now working!

---

