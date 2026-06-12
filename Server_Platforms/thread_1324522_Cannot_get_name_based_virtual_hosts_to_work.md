---
title: "Cannot get name based virtual hosts to work"
date: 2009-11-12
forum: Server Platforms
---

### Post by aajax on 2009-11-12
The Debianized method of configuring Apache looks good conceptually but I'm having great difficulty getting it to work in practice.  

I've installed a new server and my initial reconfiguration attempt is merely to prevent the default host from serving some of the system specific files (i.e., cgi and doc) but rather have them served by a specific virtual host that I define with some access restriction.

The result after configuring (see below) is that the virtual host seems not to exist.  The really troubling thing is that the only records in errorlog refer to file not found on the default server.  This of course is the desired result for the default server but it occurs when I access using the named virtual host.  I put the "NameVirtualHost *" directive in ports.conf in order separate that specification from the definition of virtual hosts.

There is no indication of any error when the server is either started or reloaded.  

The files named default and Venus that are in sites-available are shown below.  Both files have links in sites-enabled.

My revised configuration file (named default) follows:
```
# NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmsster@localhost
	
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
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

</VirtualHost>

My attempt at defining a virtual host (file named Venus) follows:
# NameVirtualHost *
<VirtualHost *>
	ServerName  venus.my.test
        ServerAlias venus
	DocumentRoot /work/WEBvenus/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /work/WEBvenus/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
#DG#		allow from all
		allow from 10.0.0
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
#DG#		Allow from all
		Allow from 10.0.0
	</Directory>

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
#DG#        Allow from 127.0.0.0/255.0.0.0 ::1/128
	Allow from 10.0.0
    </Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

</VirtualHost>
```

It turns out that I can access the virtual host by using the ServerAlias but not the ServerName.  Does that make any sense?

---

### Post by Ilalmi on 2009-11-13
Hi,

you have to assign a specific hostname or IP address to each of your virtual hosts through the VirtualHost directive. The entry <VirtualHost *> in your configuration serves every request. As a result, your first server answers everything, your second server gets nothing.

Have a look at [http://httpd.apache.org/docs/2.2/en/vhosts/](http://httpd.apache.org/docs/2.2/en/vhosts/) and [http://httpd.apache.org/docs/2.2/en/mod/core.html#virtualhost](http://httpd.apache.org/docs/2.2/en/mod/core.html#virtualhost) .

I hope that gets you further.

---

### Post by Iowan on 2009-11-13
[Here]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") is a link I've had bookmarked for awhile - hope it helps.
[Another]("http://httpd.apache.org/docs/2.0/vhosts/name-based.html") one I have bookmarked.

---

### Post by aajax on 2009-11-16
> **Ilalmi said:**
> Hi,

you have to assign a specific hostname or IP address to each of your virtual hosts through the VirtualHost directive. The entry <VirtualHost *> in your configuration serves every request. As a result, your first server answers everything, your second server gets nothing.

Have a look at [http://httpd.apache.org/docs/2.2/en/vhosts/](http://httpd.apache.org/docs/2.2/en/vhosts/) and [http://httpd.apache.org/docs/2.2/en/mod/core.html#virtualhost](http://httpd.apache.org/docs/2.2/en/mod/core.html#virtualhost) .

I hope that gets you further.

This explanation is not consistent with my finding that I can access the vhost using the name specified using ServerAlias but not with the name specified using ServerName.

Furthermore, the Apache documentation seems to suggest that the argurment of the VirtualHost statement must match some NameVirtualHost argument, which I do have.  Insofar as I don't care what interface or port the requests are received on I specified *.  It also seems to me that this is consistent with the concept of using name based virtual hosting.  In that, I want the host name on the URL to be the determining factor.

> **Iowan said:**
> [Here]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") is a link I've had bookmarked for awhile - hope it helps.
[Another]("http://httpd.apache.org/docs/2.0/vhosts/name-based.html") one I have bookmarked.

A little more testing reveals that the problem seems to be with the hostname.  In that, when I interchange the names specified on the ServerName and ServerAlias directives, venus still works and venus.my.test still fails.  Both names resolve to the correct address via my DNS.

What other property of the name might matter?

Specifying a dummy ServerName for the default virtual host seems to have corrected the problem.  If anyone can explain why please do so!

---

### Post by klnyc on 2009-12-23
> **aajax said:**
> Specifying a dummy ServerName for the default virtual host seems to have corrected the problem.  If anyone can explain why please do so!

Im still struggling with VH :(

---

