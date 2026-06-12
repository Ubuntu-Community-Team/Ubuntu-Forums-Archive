---
title: "help with settings up awstats"
date: 2013-11-12
forum: Server Platforms
---

### Post by sbjaved on 2013-11-12
I'm new to apache and i'm trying to set up **AWStats** on my ubuntu 12.04 server. I've followed the guide at Ubuntu docs [https://help.ubuntu.com/community/AWStats]("https://help.ubuntu.com/community/AWStats")

I set it up according to the instructions and awstats is able to generate initial stats from apache log successfully. I placed the links to awstats in the default virtual host file. However when I try to run *[http://192.168.0.10:8080/awstats/awstats.pl](http://192.168.0.10:8080/awstats/awstats.pl)*, I get:

[I]Error: SiteDomain parameter not defined in your config/domain file. You must edit it for using this version of AWStats. 

Setup ('/etc/awstats/awstats.conf' file, web server or permissions) may be wrong.
Check config file, permissions and AWStats documentation (in 'docs' directory).[/I]

Here is my **/etc/apache2/sites-available/default** file:
```

<VirtualHost *:8080>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/saad/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/saad/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride AuthConfig
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
	
	Alias /awstatsclasses "/usr/share/awstats/lib/"
	Alias /awstats-icon "/usr/share/awstats/icon/"
	Alias /awstatscss "/usr/share/doc/awstats/examples/css"
	ScriptAlias /awstats/ /usr/lib/cgi-bin/
	Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
	
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

The only three variables I edited in **/etc/awstats/awstats.conf** are:

```
LogFile="/var/log/apache2/access.log" 
SiteDomain="server-name.noip.org"
HostAliases="localhost 127.0.0.1 server-name.no-ip.org"
```

Let me add that the apache server is working fine and i'm able to access other pages stored on the server. Any guidance would be welcome.

---

### Post by TheFu on 2013-11-12
Haven't set this up in years, but it is still working.
I believe awstats requires each domain to create a different /etc/awstats/xxxxxxxxxxxxxx.conf file based on the domainname. Right?
**awstats.server-name.noip.org.conf** is the name you should use.
Further, local-global settings go into **awstats.conf.local** ... to override the default awstats.conf.

I remember having to change the log parsing patterns slightly to match the output from apache. I'm running ubuntu 10.04 on that box. The newer Ubuntus have switched to a different apache version ... I believe 13.10 is a HUGE change in Apache.

The thing that always got me was ensuring the process that updated the stats was owned by www-data AND that all the output dirs and files were owned by www-data.www-data to prevent permissions issues.

Is ErrorLog ${APACHE_LOG_DIR}/error.log allowed? Never seen an apache conf that allowed variable substitution like that, but my apache knowledge is pretty limited. Switched to nginx on my main sites years ago.

---

### Post by sbjaved on 2013-11-12
Moved the settings into awstats.server-name.noip.org.conf
Changed permissions of awstats.pl which updates stats and awstats.server-name.noip.org.conf to 777.
Still no dice :(

---

### Post by sbjaved on 2013-11-12
Turns out you have to edit the awstats.conf file **in addition** to the awstats.server-name.no-ip.org file to get it to work. The wiki instructions were to only edit the self created conf file. Once I edited the awstats.conf itself, it started working.

---

### Post by TheFu on 2013-11-12
> **sbjaved said:**
> Moved the settings into awstats.server-name.noip.org.conf
Changed permissions of awstats.pl which updates stats and awstats.server-name.noip.org.conf to 777.
Still no dice :(

Don't forget to fix that. Using 777 permissions anywhere on a server is a terrible, terrible, terrible idea.

---

