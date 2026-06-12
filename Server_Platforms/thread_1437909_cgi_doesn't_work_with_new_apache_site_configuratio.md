---
title: "cgi doesn't work with new apache site configuration"
date: 2010-03-24
forum: Server Platforms
---

### Post by johnysack5 on 2010-03-24
Hi

I installed apache on my local machine to test my sites. I have one problem:

I created a new site configuration in /etc/apache2/sites-available and enabled it. The problem is that cgi is not working, it just prints the content of the files. (The default location for cgi, /usr/lib/cgi-bin works without problem.)
Here is the content of the site configuration file:
```

<VirtualHost *site1:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www/site1/public_html
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/site1/public_html>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /var/www/site1/cgi-bin/
	<Directory "/var/www/site1/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/www/site1/logs/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/www/site1/logs/access.log combined

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

Does anyone have an idea what could be the problem?
Thanks in advance.

---

### Post by cdenley on 2010-03-24
```

<VirtualHost **[COLOR="Red"]*:80[/COLOR]**>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www/site1/public_html
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/site1/public_html>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /var/www/site1/cgi-bin/
	<Directory "/var/www/site1/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/www/site1/logs/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/www/site1/logs/access.log combined

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
I don't think you had a valid "VirtualHost" tag. Even if you didn't get an error from that, it certainly would not have matched any interface so it would have have used that site configuration at all.

Did you reload apache after enabling your new site configuration?
```

sudo a2ensite site1

```

It should not be possible to view the source of a cgi script. Ensure that /var/www/site1/cgi-bin cannot be accessed from any other site configuration's DocumentRoot or Alias.

---

### Post by johnysack5 on 2010-03-24
Yes, I reloaded apache when I enabled the new site configuration.

Right now there are only two site configuration files enabled: the default and the one I posted.

You are right about the virtualhost tag, I corrected that.

---

### Post by cdenley on 2010-03-24
> **johnysack5 said:**
> Yes, I reloaded apache when I enabled the new site configuration.

Right now there are only two site configuration files enabled: the default and the one I posted.

You are right about the virtualhost tag, I corrected that.

You corrected that, reloaded apache, and still get the same results? You have the default site configuration still, but haven't configured a ServerName for your new configuration? Your new configuration will never be used.

When apache receives a request, it pulls the hostname from the request's header. If there is no hostname provided, the default site configuration is used. Otherwise, it searches for a site configuration configured with that hostname as either the "ServerName" or "ServerAlias", starting with the default site, then alphabetically. If it doesn't find a site with the matching hostname, then the default site is used. You haven't configured any hostname, so the default site will always be used.

Also, I think your default site configuration allows /var/www/site1/cgi-bin to be read without script execution which allows your cgi scripts code to be viewed. This is really bad.

Probably the easiest solution would be to replace your default site configuration with your new one, assuming you don't actually use what is now the default:
```

sudo a2dissite site1
sudo mv /etc/apache2/sites-available/default /etc/apache2/sites-available/original_default
sudo mv /etc/apache2/sites-available/site1 /etc/apache2/sites-available/default
sudo /etc/init.d/apache2 reload

```

---

### Post by Ikith on 2010-03-24
Instead of adding +execcgi in that directory why not scriptalias it since its the same directory as the "default" then specify your options inside of that directory/

---

