---
title: "localhost many subdomains"
date: 2012-05-09
forum: Server Platforms
---

### Post by jason3 on 2012-05-09
Hi
I wan to make many subdomains on my localhost. I found [this tutorial]("http://thinkingnectar.com/2008/getting-ubuntu-to-work-creating-subdomain-in-localhost/") and it's working almost right.
I add three subdomains admin, cake and main. The problem is, that each of these redirect me to the same dir.
Of course in each cfg file i put diferent path (/var/www/admin, /var/www/cakephp and /var/www/main)
I run ubuntu 12.04, apache2

---

### Post by volkswagner on 2012-05-09
That how-to is missing one step.

In /etc/apache2/ports.conf you should have the following line:

```
NameVirtualHost *
```

You will need to restart apache after adding the above.
Note the above is based on how you label virtual hosts.

In the how to it is listed as
```
<VirtualHost *>
```

Some folks specify the port like:
```
<VirtualHost *:80>
```


This will tell Apache to use name based virtual hosts.

You should also verify your sites are in fact enabled by listing:
```
ls -alt /etc/apache2/sites-enabled
```

---

### Post by jason3 on 2012-05-09
ok, i already have line NameVirtualHost * 
When i change it for VirtualHost * apache throws me an error:
> root@net:/home/gh# service apache2 restart
Syntax error on line 8 of /etc/apache2/ports.conf:
Invalid command 'VirtualHost', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!

so i changed it back
result of command: ls -alt /etc/apache2/sites-enabled
> total 8
drwxr-xr-x 2 root root 4096 maj  9 12:21 .
lrwxrwxrwx 1 root root   23 maj  9 12:21 cake -> ../sites-available/cake
lrwxrwxrwx 1 root root   23 kwi 18 09:47 main -> ../sites-available/main
lrwxrwxrwx 1 root root   24 kwi 18 09:17 admin -> ../sites-available/admin
lrwxrwxrwx 1 root root   22 kwi 18 09:17 cms -> ../sites-available/cms
drwxr-xr-x 7 root root 4096 mar 10 05:53 ..


/etc/apache2/sites-available/cake:
> <VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/cakephp
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/cakephp/>
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


[COLOR="Red"]edit:[/COLOR]
i changed content of /etc/apache2/sites-available/cake (^up^) to:
> <VirtualHost *:80>
	ServerAdmin webmaster@localhost
        ServerName cake.localhost
	ServerAlias cake.pl.localhost
	DocumentRoot /var/www/cakephp
	<Directory /var/www/cakephp/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
and it works!

---

