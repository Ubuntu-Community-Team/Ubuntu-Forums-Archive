---
title: "Trouble with Apache virtual hosts"
date: 2007-04-30
forum: Server Platforms
---

### Post by erikcw on 2007-04-30
Hi all,

I've installed apache 2.2 on Feisty.  I'm trying to setup 2 virtual hosts.  The default, localhost (so I can access phpmyadmin, etc...), and my dev host, dev.mydomain.com

I've eneabled the virtual host for dev.mydomain.com (and setup my /etc/hosts file to route that domain to 127.0.0.1).  It works great - but I can no longer access localhost.

default
> 
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
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

mysite.com.conf
> 
#
#  Example.com (/etc/apache2/sites-available/www.example.com)
#
<VirtualHost dev.mysite.com>
        ServerAdmin erik@localhost
        ServerAlias [www.dev.mysite.com](www.dev.mysite.com)

        # Indexes + Directory Root.
        DirectoryIndex index.html
        DocumentRoot /home/lybp/public_html/

        # CGI Directory
        #ScriptAlias /cgi-bin/ /home/lypb/public_html/cgi-bin/
        #<Location /cgi-bin>
        #        Options +ExecCGI
        #</Location>


        # Logfiles
        ErrorLog  /home/lybp/logs/error.log
        CustomLog /home/lybp/logs/access.log combined
</VirtualHost>

/etc/hosts
> 
127.0.0.1	localhost
127.0.1.1	turbo
127.0.0.1	dev.mysite.com [www.dev.mysite.com](www.dev.mysite.com)

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


What do I have to do to make them play nicely?

Thanks!
Erik

---

### Post by iiibill on 2007-05-13
You say you want to use named virtual hosts, but no where in your virtual host definition do you tell it what name to use.  You need to add a servername to the virtual host definition.  Something like:

  <virtualhost *>
    servername foo.bar.com
    ...
 </virtualhost>

 <virtualhost *>
   servername baz.faz.com
   ...
 </virutalhost>

---

### Post by pjrodz on 2007-05-17
> **iiibill said:**
> You say you want to use named virtual hosts, but no where in your virtual host definition do you tell it what name to use.  You need to add a servername to the virtual host definition.  Something like:

  <virtualhost *>
    servername foo.bar.com
    ...
 </virtualhost>

 <virtualhost *>
   servername baz.faz.com
   ...
 </virutalhost>

how do you assign servernames to localhost sites? thanks!

---

### Post by erikcw on 2007-05-20
> **iiibill said:**
> You say you want to use named virtual hosts, but no where in your virtual host definition do you tell it what name to use.  You need to add a servername to the virtual host definition.  Something like:

  <virtualhost *>
    servername foo.bar.com
    ...
 </virtualhost>

 <virtualhost *>
   servername baz.faz.com
   ...
 </virutalhost>

I'm now getting this warning:
> 
sudo /etc/init.d/apache2 restart
 * Forcing reload of web server (apache2)...                                                                                                                                                                   apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun May 20 13:20:38 2007] [warn] VirtualHost localhost:0 overlaps with VirtualHost dev.loweryourbidprice.com:0, the first has precedence, perhaps you need a NameVirtualHost directive
[Sun May 20 13:20:38 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun May 20 13:20:48 2007] [warn] VirtualHost localhost:0 overlaps with VirtualHost dev.loweryourbidprice.com:0, the first has precedence, perhaps you need a NameVirtualHost directive
[Sun May 20 13:20:48 2007] [warn] NameVirtualHost *:0 has no VirtualHosts



Here are the changes I made to the config file:
> 
#NameVirtualHost *
<VirtualHost localhost>
    ServerAdmin webmaster@localhost
    servername localhost

    DocumentRoot /var/www/


I'm missing something.

---

### Post by orozcovision on 2007-05-23
Try this:

#//---------------------------------------------
NameVirtualHost *:80
<VirtualHost *:80>
   ServerAdmin webmaster@localhost
   ServerName localhost
</VirtualHost>
#----------------------------------------------//

---

### Post by erikcw on 2007-05-24
Nope, that didn't work either.  localhost still uses the document root of the other virtualhost.

Don't know if this is info will help...:
> 
$ sudo /etc/init.d/apache2 restart
 * Forcing reload of web server (apache2)...                                                                                                                                                                   apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu May 24 09:19:43 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu May 24 09:19:53 2007] [warn] NameVirtualHost *:0 has no VirtualHosts


---

### Post by darf on 2007-11-22
Are you starting apache with "-D DEFAULT_VHOST"? if so remove it and restart.

---

