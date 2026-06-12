---
title: "can't set up virtual host for web site testing"
date: 2009-05-03
forum: Server Platforms
---

### Post by quixote on 2009-05-03
I just cannot get my server to stop going to my public website when I want it to go to my test site.  I'd like to be able to work on, for instance, "molvray.com" locally, and then upload the files. However, if I have the site on localhost, then all the links, such as molvray.com/images, go straight back to the real site.  So I want a virtual host that I can call "molvray.com" while I'm testing.  Once I'm done testing, I want to go back to the normal condition where "molvray.com" refers to the public site.

Okay.  So far, so good.  There's just the thing here at [ApacheMySQLPHP - Community Docs]("https://help.ubuntu.com/community/ApacheMySQLPHP#head-8c16bcd2517fa5b9fa35d616f00d3bb59e981373").

Except no matter what I do, I cannot get it to work.  Typing the URL "molvray.com" always goes to the real site, not my test site on localhost.  Why?  Why, why why??

Here's what I've done:

"molvray.com" in /etc/apache2/sites-available/molvray.com
```
# Virtual host
NameVirtualHost *
#	ServerName www.molvray.com
#	DocumentRoot /var/www/              /*I'm just using the default doc root*/
#	ServerAdmin webfoot@molvray.com

<VirtualHost *>
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>

	ServerAdmin webfoot@molvray.com
	ServerName www.molvray.com
	ServerAlias molvray.com
	DocumentRoot /var/www/

	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

#	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
#	<Directory "/usr/lib/cgi-bin">
#		AllowOverride None
#		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
#		Order allow,deny
#		Allow from all
#	</Directory>
#
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

</VirtualHost>

```

The only thing I changed in the "default" sites-available entry was VirtualServer * (instead of *:80 which kept giving error messages that "NameVirtualHost *:80 has no VirtualHosts")

I also commented out the NameVirtualHost line in ports.conf, also to get rid of an error message.
```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default

#NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>
```

I used "$sudo a2dissite default" to stop that, and "$sudo a2ensite molvray.com" to start the new one.  I reloaded apache2.  No luck.  I rebooted.  Still no luck.

I must be missing some perfectly obvious step, but I'm damned if I can see it.  I hope someone can help!

---

### Post by bluefrog on 2009-05-04
/etc/hosts

molvray.com must be the name of one of your IP

---

### Post by quixote on 2009-05-04
bluefrog- I tried that, or I think I did.  
```
127.0.0.1	localhost
127.0.1.1	sphinx           #my computer name
127.0.0.1       molvray.com

```

I also tried "127.0.0.1 localhost molvray.com"  and giving the virtual host its own IP: "127.0.2.1 molvray.com"

None of those seemed to have any effect, which mystified me.  Localhost was still localhost (which was good!), and molvray.com still always went to the great wide world.

I use DHCP for my network, in case that's relevant.

Added: what I haven't done is give molvray.com an IP *after* figuring out the new "sites-available" way of doing things.  I'll go try that right now.

---

### Post by quixote on 2009-05-04
Yup, that was it.  I'd removed the "molvray.com" from /etc/hosts, because it didn't seem to do anything.  But now that I have the correct info in sites-available, just putting molvray.com after localhost is all it seems to need.

Thanks!

(Note to anyone who might be trying the same thing, don't forget to restart networking (sudo /etc/init.d/networking restart) *and* to reload the page in the browser (shift-ctrl-r).  It took me a few tries before I figured out why Firefox kept giving me the local page after I'd switched back to non-testing mode ....)

---

