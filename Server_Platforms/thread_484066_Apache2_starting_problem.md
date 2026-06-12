---
title: "Apache2 starting problem"
date: 2007-06-25
forum: Server Platforms
---

### Post by incolumus on 2007-06-25
I've been walking around anda I haven't got the solution (maybe I'm too newbie on this :( ) Ok, let go!!

I've installed apache2+php+mysql+... two days ago and everything works great! I made an no-ip account to access my web from outside and it works! But today I came across a serious problem when trying to access my web from outside: "Not Found" Ok, maybe apache or the server is down, no problem, just getting home and starting it again:

```
sudo /usr/sbin/apache2ctl restart
```

and all what I get is:

```
Syntax error on line 6 of /etc/apache2/sites-enabled/000-default:
The port number "http://MYDOMAIN.no-ip.info" is outside the appropriate range (i.e., 1..65535).
```

This is the file referenced:
```

NameVirtualHost EMO
<VirtualHost MY_PUBLIC_IP>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www
	ServerName http://MYDOMAIN.no-ip.info
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
		#RedirectMatch ^/$ /apache2-default/
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
	ServerSignature On

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
Of course, where it is said "MY_PUBLIC_IP" it's written my public ip with numbers...

Thanks in advance to all!
incolumus

---

### Post by MJN on 2007-06-26
Get rid of the **http://** prefix in the servername directive.
 
(It sees the **:** as a name/port delimiter and hence is thinking your server name is **http** and your port is **MYDOMAIN** which is probably not a number between 1 and 65535.)
 
Incidentally, did you spot that it mentioned which line (6) was at fault? This is always worth taking into account - it'd no guarantee but it's always a good starting point at working out the problem.
 
Mathew.

---

