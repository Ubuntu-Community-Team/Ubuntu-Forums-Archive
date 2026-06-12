---
title: "DaviCal woes"
date: 2010-08-12
forum: Server Platforms
---

### Post by clegends on 2010-08-12
Hi folks, am having trouble setting up a localhost DaviCal server. I've followed the directions here: [http://ubuntuguide.org/wiki/DAViCal_current_version](http://ubuntuguide.org/wiki/DAViCal_current_version)

And everything seems to be working, but when I go to: [http://localhost/cal](http://localhost/cal)

I get the "Not Found" page. How do I tweak this to use it locally from my computer? Have searched and tried to follow various tutorials, but no luck.

What I'm trying to do is setup a CalDav server locally on my computer so I can interface Thunderbird with it. The reason being then I can sync my Android phone with the CalDav server on my computer, thus syncing my Thunderbird calendar with it. Android is great, but currently the only ways to sync your calendar is to go through google's servers (not interested) or use the new CalDav sync software from the market... which is what I'm trying to do. Anyway, would appreciate any help to get this server up and running locally. Cheers.

---

### Post by Xinerama on 2011-01-03
I would also like to do this.  I followed basically the same page that the OP did, however I made this modification to my /etc/apache2/sites-available/default
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName "el1as.homelinux.org"
	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
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

[color=red]
<Directory /usr/share/davical/htdocs/>
     AllowOverride None
     Order allow,deny
     Allow from all
 </Directory>
 php_value include_path /usr/share/awl/inc
 php_value magic_quotes_gpc 0
 php_value register_globals 0
 php_value open_basedir 1
 php_value error_reporting "E_ALL & ~E_NOTICE"
 php_value default_charset "utf-8"
[/color]
</VirtualHost>

```

I can't go to el1as.homelinux.org/cal for some reason though.
How're you supposed to set this up with an already existing webserver running?

---

