---
title: "Newb: Please help me set up virtual hosting"
date: 2008-03-17
forum: Server Platforms
---

### Post by Smartin on 2008-03-17
Hi,

I'm hopingt some kind soul will get me past this, I think it's something fairly simple... I have tried to follow the various threads here but I'm still messing something up...

I'm wanting to host two sites on my Gutsy box, on *one IP address*.
The sites are [www.p4pixel.com](www.p4pixel.com) and [www.trackrooms.co.uk](www.trackrooms.co.uk). At the moment both addresses are showing the p4pixel site...

First, I get this from the terminal:
```

smartin@p4pixel:~$ sudo a2ensite
[sudo] password for smartin:
Which site would you like to enable?
Your choices are: default default~ trackrooms
Site name? default
Site default installed; run /etc/init.d/apache2 reload to enable.
smartin@p4pixel:~$ sudo a2ensite
Which site would you like to enable?
Your choices are: default default~ trackrooms
Site name? trackrooms
This site is already enabled!
smartin@p4pixel:~$ sudo /etc/init.d/apache2 reload
 * Reloading web server config apache2                                          7274
[Mon Mar 17 14:19:31 2008] [warn] NameVirtualHost 127.0.0.1:80 has no VirtualHosts
[Mon Mar 17 14:19:31 2008] [warn] NameVirtualHost 127.0.0.1:443 has no VirtualHosts
[Mon Mar 17 14:19:31 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Mon Mar 17 14:19:31 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Mon Mar 17 14:19:31 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Mon Mar 17 14:19:31 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Mon Mar 17 14:19:31 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
                                                                         [ OK ]
smartin@p4pixel:~$ 

```

I have the following (key?)files:
/etc/apache2/apache2.conf
/etc/apache2/httpd.conf
/etc/apache2/sites-available/default
/etc/apache2/sites-available/trackrooms
/etc/apache2/sites-enabled/000-default
/etc/apache2/sites-enabled/p4pixel
/etc/apache2/sites-enabled/trackrooms

/etc/apache2/apache2.conf contains rather a lot but at the end I have:
```

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

# Listen for virtual host requests on all IP addresses
NameVirtualHost 127.0.0.1:80
NameVirtualHost 127.0.0.1:443
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/[^.#]*

```

/etc/apache2/httpd.conf contains nothing at all.

/etc/apache2/sites-available/default contains:
```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@p4pixel.com
	
	DocumentRoot /var/www/
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

/etc/apache2/sites-available/trackrooms contains:
```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@trackrooms.co.uk
	
	DocumentRoot /var/www/trackrooms
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/trackrooms/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
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

/etc/apache2/sites-enabled/000-default contains:
```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@p4pixel.com
	
	DocumentRoot /var/www/
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

/etc/apache2/sites-enabled/p4pixel contains:
```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@p4pixel.com
	
	DocumentRoot /var/www/
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

/etc/apache2/sites-enabled/trackrooms contains:
```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@p4pixel.com
	
	DocumentRoot /var/www/
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

Did I miss anything?

Thanks in advance!

Simon

---

### Post by nebajoth on 2008-04-12
Having essentially the same problem.  Different URLs, of course. :D

---

### Post by songshu on 2008-04-12
i guess you have both sites in a different folder under /var/www/

if so you could try to set this for 
/etc/apache2/sites-enabled/trackrooms

DocumentRoot /var/www/trackrooms

---

### Post by Smartin on 2008-04-12
> **nebajoth said:**
> Having essentially the same problem.  Different URLs, of course. :D

Hi,

That's interesting!

I had convinced myself that it was my setup and that I needed to tear down the whole box and do a re-install.

Perhaps I'm not the only one after all. Let me know if you find a solution! :-)

Simon

---

### Post by Smartin on 2008-04-12
> **songshu said:**
> i guess you have both sites in a different folder under /var/www/

if so you could try to set this for 
/etc/apache2/sites-enabled/trackrooms

DocumentRoot /var/www/trackrooms

Hi,

I have tried this but to no avail...

Simon

---

### Post by Smartin on 2008-04-12
Hi,

You might want to have a look at my thread on Howtoforge...

[http://howtoforge.org/forums/showthread.php?t=21483](http://howtoforge.org/forums/showthread.php?t=21483)

Simon

---

### Post by conjur3r on 2008-04-12
Gday

You are missing [ServerName]("http://httpd.apache.org/docs/2.0/mod/core.html#servername") directives in your site configs.  This tells apache which site to serve for the requested domain.  While you're at it, also add ServerAlias directives too.  For example:

/etc/apache2/sites-available/trackrooms 
```

<VirtualHost *>
	ServerAdmin webmaster@trackrooms.co.uk
[COLOR="Red"]        ServerName trackrooms.co.uk
        ServerAlias www.trackrooms.co.uk
[/COLOR]
```

---

### Post by Smartin on 2008-04-19
> **conjur3r said:**
> Gday

You are missing [ServerName]("http://httpd.apache.org/docs/2.0/mod/core.html#servername") directives in your site configs.  This tells apache which site to serve for the requested domain.  While you're at it, also add ServerAlias directives too.  For example:

/etc/apache2/sites-available/trackrooms 
```

<VirtualHost *>
	ServerAdmin webmaster@trackrooms.co.uk
[COLOR="Red"]        ServerName trackrooms.co.uk
        ServerAlias www.trackrooms.co.uk
[/COLOR]
```

Yesss!! :-) Sorry for the delayed response but you fixed it!

I thought it had to be something simple.

Thanks mate! Owe you one!

Simon

---

