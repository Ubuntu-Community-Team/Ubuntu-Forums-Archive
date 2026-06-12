---
title: "Help with 'Name Based Virtual Hosts' on Apache2 (Feisty)"
date: 2007-05-23
forum: Server Platforms
---

### Post by a.d.gardiner on 2007-05-23
Hey all,

I'm pretty confused about how to get virtual hosts going on my Apache2 server (Ubuntu feisty).

I've been through the Apache2 documentation and also the stuff at [http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html), plus the forum's here, but I seem to be getting conflicting information :(

I want to configure my Apache2 to run two sites, possibly more in future, with name-based virtual hosting. For example: [www.chevinstaffportal.co.uk](www.chevinstaffportal.co.uk) and [www.alexandergardiner.co.uk](www.alexandergardiner.co.uk) but I'm  not entirely sure which files I need to edit?

I'm under the impression I need to leave my 'httpd.conf' alone, and also leave the contents of 'sites-enabled', but to create a seperate file for each site in 'sites-available'?

Thing is I'm not entierly sure what the code needs to look like in each of those entries.

The only file I currently have in sites-available - named 'default' reads like this:

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/phpBB2/
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

Ideally I want to host the contents at /var/www/phpBB2/ for [www.chevinstaffportal.co.uk](www.chevinstaffportal.co.uk) and /var/www/alexandergardiner/ for [www.alexandergardiner.co.uk](www.alexandergardiner.co.uk).

Can anybody help? I've been stuck for a good while on this. ;)

---

### Post by turinglabs on 2007-05-23
> **a.d.gardiner said:**
> Hey all,
I'm under the impression I need to leave my 'httpd.conf' alone, and also leave the contents of 'sites-enabled', but to create a seperate file for each site in 'sites-available'?

Thing is I'm not entierly sure what the code needs to look like in each of those entries.

Ideally I want to host the contents at /var/www/phpBB2/ for [www.chevinstaffportal.co.uk](www.chevinstaffportal.co.uk) and /var/www/alexandergardiner/ for [www.alexandergardiner.co.uk](www.alexandergardiner.co.uk).


You've got the right idea - you create one file for each site in 'sites-available', then create a symlink to this file in 'sites-enabled'. Ubuntu/Debian have some nice commands that deal with the links automatically, namely 'a2ensite' (creates a link) and 'a2dissite' (deletes a link). 

In your situation, create a file called  '001-chevinstaffportal.co.uk' in sites-available, then run 'a2ensite 001-chevinstaffportal.co.uk' (or just run a2ensite for interactive mode), then run '/etc/init.d/apache2 reload' . The file would (minimally) look like this:

<VirtualHost *>
DocumentRoot /var/www/phpBB2
ServerName [www.chevinstaffportal.co.uk](www.chevinstaffportal.co.uk)
ServerAlias chevinstaffportal.co.uk
ErrorLog /var/log/apache2/chevin-error.log
TransferLog /var/log/apache2/chevin-access.log
</VirtualHost>

Most of the Apache directives can be used inside virtual hosts.

This gets a bit more complicated if you are running apache on multiple ports on the same host - then you have to specify the port numbers in the VirtualHost declarations (SSL is the most common need for this), like <VirtualHost *:80>.

Your next site's file would be named 002-alexandergardiner.co.uk, for example (you can name them anything, as long as it makes sense to you).

HTH,

Doug

---

### Post by a.d.gardiner on 2007-05-23
:) Thanks for the information, I'll have a look when I'm back in the morning... the cleaner is about to kick me out of my office!

I tired to SSH in before from home and edit things with VI but i made a bit of a mess. lol

---

### Post by a.d.gardiner on 2007-05-24
Okay I think I'm getting somewhere, but still seem to be a little stuck.

First I created the relevant files following the example above in 'sites-available', then I symlinked them with the 'a2ensite' command to enable each site in their respective folders.

My code reads:

```
<VirtualHost *>
DocumentRoot /var/www/phpBB2/
ServerName www.chevinstaffportal.co.uk
ServerAlias chevinstaffportal.co.uk
ErrorLog /var/log/apache2/chevin-error.log
TransferLog /var/log/apache2/chevin-access.log
</VirtualHost>
```

(In reality the only one which is active at present is 'www.chevinstaffportal.co.uk', I still need to move my other sites over)

I then used 'a2dissite' to disable the file 'default' which was already sat in 'sites -available' from installing apache2.

However when I access 'www.chevinstaffportal.co.uk' where I would imagine the URL of the site would appear in the browser, the IP address of my connection appears '81.149.22.40' instead?

I'm guessing I might have something else that needs installing? Some kind of DNS or something? ;)

---

