---
title: "Apache 2.4 not Responding to Second .conf File"
date: 2014-04-11
forum: Server Platforms
---

### Post by batymahn on 2014-04-11
Hi Guys,
I'm running Ubuntu 13.10, with Apache 2.4, and I want several name-based virtual hosts.  The first host works as I expect but the second, which was a direct copy of the first .conf file, just changing the directory, site and file names, only serves the Apache "It Works" page.  It should serve a initial Wordpress site.  Both folder are group-owned by www-data and are chmod 775.

<VirtualHost *:80>

ServerName two.example.org

DocumentRoot /var/www/twoExample

ServerAdmin [email]chris@aacil.org[/email]

   <Directory /var/www/twoExample >
      Options All
      AllowOverride All
      Require all granted
    </Directory>


</VirtualHost>


 I  added each site to /etc/hosts:

127.0.1.1  one.example.org two.example.org

'one.example.org' works fine locally and remotly but two.example.org only works locally.  I've tried everything I  could think of and the logs are not helpful in.

Any ideas?

Thanks,.

Chris

---

### Post by Habitual on 2014-04-11
did you restart apache?

---

### Post by batymahn on 2014-04-14
Reloaded, restarted, rebooted - everything.  Something is preventing Apache from reading my additional .conf files.

Grrr.   

Chris

---

### Post by batymahn on 2014-04-22
In desperation I put all my virtual domains in 000-default.conf:

<VirtualHost *:80>
	# The ServerName directive sets the request scheme, hostname and port that
	# the server uses to identify itself. This is used when creating
	# redirection URLs. In the context of virtual hosts, the ServerName
	# specifies what hostname must appear in the request's Host: header to
	# match this virtual host. For the default virtual host (this file) this
	# value is not decisive as it is used as a last resort host regardless.
	# However, you must set it for any further virtual host explicitly.
	ServerName apache.aacil.org

	ServerAdmin webmaster@localhost
	DocumentRoot /var/www

	# Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
	# error, crit, alert, emerg.
	# It is also possible to configure the loglevel for particular
	# modules, e.g.
	#LogLevel info ssl:warn

	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined

	# For most configuration files from conf-available/, which are
	# enabled or disabled at a global level, it is possible to
	# include a line for only one particular virtual host. For example the
	# following line enables the CGI configuration for this host only
	# after it has been globally disabled with "a2disconf".
	#Include conf-available/serve-cgi-bin.conf
</VirtualHost>

<VirtualHost *:80>
    ServerName oldsite.aacil.org
    DocumentRoot /var/www/oldsite
    <Directory /var/www/oldsite>
        Options -Indexes
        Require all granted
        DirectoryIndex index.php
        AllowOverride All
    </Directory>

</VirtualHost> 

<VirtualHost *:80>
    ServerAdmin [email]chris@aacil.org[/email]
    ServerName alpha.aacil.org
#    ServerAlias alpha.aacil.org

    DocumentRoot /var/www/alpha

    <Directory /var/www/alpha>
        DirectoryIndex index.php
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

	ErrorLog /var/log/apache2/alpha.error.log
	LogLevel warn
	CustomLog /var/log/apache2/alpha.access.log combined

</VirtualHost> 

<VirtualHost *:80>
    ServerName newsite.aacil.org
    DocumentRoot /var/www/newsite
    <Directory /var/www/newsite>
        Options -Indexes
        Require all granted
        DirectoryIndex index.php index.html
        AllowOverride All
    </Directory>

</VirtualHost> 

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet1

Every domain works except alpha.aacil.org, but it works when I access it locally.  error.log doesn't even see the attempts to accesss alpha.aacil.org remotely.  It's almost like Apache2.4 can only handle 2 domains at a time?

Chris

---

### Post by NetVicious on 2014-04-23
The second config filename ends in ".conf" ?

On 2.4 all config filenames should end in ".conf". Example "myserver**_.conf_**"

---

### Post by batymahn on 2014-04-23
Yep, thought of that, but it doesn't matter now because all my domains are in 000-default.conf now.  But thanks.

The thing of it is that I've run into the same issue on serveral Ubuntu 13.10 installs.  I'm tempted to go back to Debian

Chris

---

