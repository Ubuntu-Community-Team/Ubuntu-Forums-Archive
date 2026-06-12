---
title: "Named Virtual Hosts in Apache"
date: 2006-12-25
forum: Server Platforms
---

### Post by bullines on 2006-12-25
Greetings!

I'm running a clean Edgy install.  I'm trying to get named virtual hosts running and I'm having some problems.  The sole purpose is for development, so any sites on this computer won't be available to the outside world...just the internal LAN.

Here's my "default" file in sites-available:

```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
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

I've attempted to add a new test site, which should resolve to [www.test.cvb](www.test.cvb).  This is my "test" file in sites-available:

```

NameVirtualHost *

<VirtualHost *:80>
   ServerName test
   DocumentRoot /var/www/test/
</VirtualHost>

```

I've issued the 'a2ensite test' command and restarted Apache.  However, when I attempt to go to [www.test.cvb](www.test.cvb), I get a directory listing of /var/www.  Is there something that I'm missing?  Thanks in advance.

---

### Post by kidders on 2006-12-25
Hi there,

Your virtual host should be called test.cvb, not [www.test.cvb](www.test.cvb) (assuming your default server address is "cvb"). See if that shows you what you're expecting. Incidentally, afaik, you should probably delete the duplicate "NameVirtualHost *" directive.

---

### Post by bullines on 2006-12-26
I've changed my "test" file in sites-available to:

```

<VirtualHost *:80>
   ServerName test.cvb
   DocumentRoot /var/www/test/
</VirtualHost>

```

Ran 'a2ensite' and restarted Apache again, but to no avail.  It still just lists the contents of /var/www when I try test.cvb or [www.test.cvb](www.test.cvb), regardless of whether I try from the Ubuntu machine or a WinXP machine on the LAN.  Do I also need to do something with /etc/hosts?  Right now, it currently looks like this:

```

127.0.0.1 localhost.localdomain localhost ubuntu
127.0.0.1 www.test.cvb
127.0.0.1 www.test2.cvb
127.0.0.1 www.test3.cvb

# The following lines are desirable for IPv6 capable hosts
::1 ip6-locahost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

What I find also find strange is that I have phpMyAdmin installed and going to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) works just fine.

:-k

---

### Post by eric_stewart on 2006-12-26
> **bullines said:**
> Greetings!

I'm running a clean Edgy install.  I'm trying to get named virtual hosts running and I'm having some problems.  The sole purpose is for development, so any sites on this computer won't be available to the outside world...just the internal LAN.

Here's my "default" file in sites-available:

```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
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

I've attempted to add a new test site, which should resolve to [www.test.cvb](www.test.cvb).  This is my "test" file in sites-available:

```

NameVirtualHost *

<VirtualHost *:80>
   ServerName test
   DocumentRoot /var/www/test/
</VirtualHost>

```

I've issued the 'a2ensite test' command and restarted Apache.  However, when I attempt to go to [www.test.cvb](www.test.cvb), I get a directory listing of /var/www.  Is there something that I'm missing?  Thanks in advance.

I'm not an expert on this by any means, but I'm hosting 3 sites on my home Ubuntu Edge Eft box.  I'm using Apache-perl and Apache-ssl.  I think your missing the ServerAlias directive.  I'm hosting [www.stewart-clan.net;](www.stewart-clan.net;) [www.breezy.ca;](www.breezy.ca;) [www.intermediatemusicsubjectcouncil.org](www.intermediatemusicsubjectcouncil.org) on my site.  Here's a partial <i>/etc/apache-perl/httpd.conf</i> file:


<VirtualHost *:80>
    ServerName [www.breezy.ca](www.breezy.ca)
    ServerAlias breezy.ca *.breezy.ca
    DocumentRoot /var/www
 </VirtualHost>

<VirtualHost *:80>
    ServerName [www.stewart-clan.net](www.stewart-clan.net)
    ServerAlias stewart.clan.net *.stewart-clan.net
    DocumentRoot /var/www/stewart-clan.net
</VirtualHost>
<VirtualHost *:80>
    ServerName [www.intermediatemusicsubjectcouncil.org](www.intermediatemusicsubjectcouncil.org)
    ServerAlias intermediatemusicsubjectcouncil.org *.intermediatemusicsubjectcouncil.org
    DocumentRoot /var/www/intermediatemusicsubjectcouncil.org
</VirtualHost>

It works fine.  Another thing that comes to mind is that according to the FAQ at [www.apache.org](www.apache.org), apparently (and here I prove that I'm no expert!) HTTP v1.1 is required on the web client since it is the client who sends the initial request...this in turn identifying the site being connected to.  Clearly ancient browsers will not work.  For more information on this feature, navigate over to [http://httpd.apache.org/docs/1.3/vhosts/name-based.html](http://httpd.apache.org/docs/1.3/vhosts/name-based.html)  on the official Apache.org website.

Note that this feature will <b>not</b> work with sites accessed over SSL (encrypted Secure Sockets Layer)since the HTTP request must be transmitted in the clear in order to be differentiated.

---

### Post by Brazen on 2006-12-26
change 'NameVirtualHost' and your default virual host to '*:80' instead of just '*' .  Alternatively, drop the ':80' off your test virtual host.

Also use Dapper instead of Edgy for a production server.

---

### Post by bullines on 2006-12-26
Thanks for the help, everyone! :)  I changed my "test" in sites-available to:

```

<VirtualHost *>
   ServerName www.test.cvb
   ServerAlias test.cvb *.test.cvb
   DocumentRoot /var/www/test
</VirtualHost>

```

All is working now.  ServerAlias was the ticket.  Thanks again :)

---

### Post by eric_stewart on 2006-12-26
Good news.  Got to love these forums!  While we should all learn from our mistakes it's much more fun learning from the mistakes of others!

Eric
webmaster 
[www.breezy.ca](www.breezy.ca)  <-- my hobby website using Apache, Drupal CMS, etc.

---

