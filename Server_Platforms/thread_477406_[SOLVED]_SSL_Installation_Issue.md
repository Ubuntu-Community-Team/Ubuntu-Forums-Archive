---
title: "[SOLVED] SSL Installation Issue"
date: 2007-06-18
forum: Server Platforms
---

### Post by efriese on 2007-06-18
I'm sure this is an easy fix, but I need some help. I've installed SSL for apache2 and following some advice from this board. My problem is when I try to visit a site via https, it prompts me to download the php file instead of viewing the page. Does anyone know why this would be happening?

---

### Post by carcioni on 2007-06-18
Be sure you have something like:

<IfDefine PHP5>
LoadModule php5_module        modules/libphp5.so
</IfDefine>

in a configuration file that is being loaded. (httpd.conf or httpd-php.conf),
and that the mime type is set for PHP.

AddType application/x-httpd-php .php .php3 .php4

This last line tells apache to treat .php files as a known executable entity, and should look for a handler in its module list to execute the file with.

---

### Post by efriese on 2007-06-18
Where do I add that in Ubuntu 6.06? I tried adding it to apache2.conf and it didn't help. httpd.conf is empty. Is there another config file I'm missing?

Thanks!

---

### Post by efriese on 2007-06-19
Any ideas?

---

### Post by dfreer on 2007-06-19
What does your /etc/apache2/sites-enabled/default look like?

---

### Post by efriese on 2007-06-28
Sorry for the long wait...

```

<VirtualHost *:80>
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

---

### Post by sgla1 on 2007-06-28
See: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html")
Look for "a2enmod"--this is how Ubuntu (and debian) load modules into apache.  It's a bit "unusual" compared to redhat, for example.

If you list out /etc/apache2/ you will see two dirs: mods-available and mods-enabled.  If you read the scripts there that relate to the module you're interested in you will see where Ubuntu and debian put their configuration options--they're not in the main apache2.conf file.

---

### Post by efriese on 2007-06-29
The PHP5 module is enabled. I looked at thePHP5 script and all is does it load the lib file. I don't think it's a module problem because PHP works fine on HTTP. Its only on HTTPS that PHP is not parsing. It's asking me if I want to download the php file I'm trying to view.

When I installed ssl, I copied /etc/apache2/sites-available/default into another file, named it ssl, and made changes. Here's that file:

```

NameVirtualHost *:443
<VirtualHost *:443>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www
	SSLEngine On
	SSLCertificateFile /etc/apache2/ssl/apache.pem
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
	<IfDefine PHP5>
	LoadModule php5_module modules/libphp5.so
	</IfDefine>

</VirtualHost>

```

Any other ideas? Thanks for the help!

---

### Post by ntom-taylor on 2007-07-01
I recently wrote a article detailing the installation of PHP5, MySQL 5, Apache2, SSL and PDO for ubuntu, the SSL section is comprehensive.

Its a collection of lots of different tutorial / resource sites i've used int the past, basically trying to bundle all the installations into one easy blog post:

[http://www.theatons.com/blog/2007/07/01/ubuntu-install-php5-mysql-apache2-ssl-pdo-pdo_mysql/#5]("http://www.theatons.com/blog/2007/07/01/ubuntu-install-php5-mysql-apache2-ssl-pdo-pdo_mysql/#5")

---

### Post by efriese on 2007-07-02
I followed your tutorial on configuring ssl, and it was the same as what I did when I first installed it. The only difference was editing the ports.conf file. When I added the Listen 443 line and restarted, it said that the port was already in use.

 I think SSL is working fine. Whenever I go to an html page in HTTPS it works and the certificate looks good. The problem is going to a page written in PHP. It gives me a download prompt instead of serving the page. The crazy thing is PHP works fine for HTTP.

When I installed apache-ssl from synaptic, did it create a separate instance of apache for ssl? It created /etc/apache-ssl and that directory has a httpd.conf file. I tried adding a <IfDefine> line to load PHP5, adding a AddType for the .php extension, and also adding a AddHandler for .php but it still doesn't work.

I'm really stumped here and I appreciate all of the help I've receive so far!

---

### Post by efriese on 2007-07-09
I still haven't been able to make this work. Should I completely remove apache and then reinstall everything?

---

### Post by efriese on 2007-07-09
The solution was to remove apache-ssl. Thanks for everyone's help!

---

