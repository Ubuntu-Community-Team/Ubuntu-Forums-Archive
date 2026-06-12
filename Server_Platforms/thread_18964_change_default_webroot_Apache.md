---
title: "change default webroot Apache"
date: 2005-03-09
forum: Server Platforms
---

### Post by lartan on 2005-03-09
Hi,

First of all, I am new to Ubuntu and like it already!!
I have an Ubuntu server, which was installed using a 'custom' installation (so no GUI). Now I would like to configure the apache web server to serve my homepage. My question is: How can I change the default webroot location?

The current default webroot is: /var/www/
I like to change this to: /home/arnejol/public_html (arnejol is a user on my system)
So I want that [http://localhost](http://localhost) points to /home/arnejol/public_html/ instead of /var/www/

I can't find how to do this, can anyone help me out?? My guess is to edit the /etc/apache2.conf file but I can't find what to edit...

---

### Post by lartan on 2005-03-09
[QUOTE=lartan]Hi,

First of all, I am new to Ubuntu and like it already!!
I have an Ubuntu server, which was installed using a 'custom' installation (so no GUI). Now I would like to configure the apache web server to serve my homepage. My question is: How can I change the default webroot location?

The current default webroot is: /var/www/
I like to change this to: /home/arnejol/public_html (arnejol is a user on my system)
So I want that [http://localhost](http://localhost) points to /home/arnejol/public_html/ instead of /var/www/

I can't find how to do this, can anyone help me out?? My guess is to edit the /etc/apache2.conf file but I can't find what to edit...[/QUOTE]
 I just foud the answer on this form in this thread:
[http://www.ubuntuforums.org/showthread.php?t=13490&highlight=documentroot](http://www.ubuntuforums.org/showthread.php?t=13490&highlight=documentroot)

The solution is to change the DocumentRoot in /etc/apache2/sites-available/default
change /var/www/ to /home/username/public_html

So simple...

---

### Post by jdonnell on 2005-03-10
I believe userdir is turned on by default on ubuntu so you can also go to
[http://localhost/~username/](http://localhost/~username/)

and this will go to /home/*/public_html

You can see the config for this in 
/etc/apache2/mods-available/userdir.conf

---

### Post by mr_crimp on 2005-11-04
[QUOTE=lartan]
The solution is to change the DocumentRoot in /etc/apache2/sites-available/default
change /var/www/ to /home/username/public_html

So simple...[/QUOTE]

I would also like to change the DocumentRoot from /var/www/ to /home/me/webpages/. So I changed the the /etc/apache2/site-avalible/default to this:

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/me/webpages/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
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

But that does not work. When I type [http://localhost](http://localhost) in my browser I get this error site (403 Forbidden): 
Forbidden
You don't have permission to access / on this server.
Apache/2.0.54 (Ubuntu) PHP/4.4.0-3 Server at localhost Port 80

This file is the onlyone I have edited after I installed Apache. Do I have to change other files? 

Does anyone have any idea what is going wrong?

---

### Post by gnottage on 2006-01-10
mr_crimp, try changing this as well:

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/me/webpages/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory [COLOR="Red"]**/var/www/**[/COLOR]>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

...

```

the bit in red if you didn't see it!

---

