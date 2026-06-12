---
title: "Finalizing Apache2 set-up. One little glitch"
date: 2008-06-01
forum: Server Platforms
---

### Post by JameoPotato on 2008-06-01
I didn't get a whole lot of help down in beginner talk cause I think is a little more for the server experts type of question which I think has an easy solution... so here it is:

I have  FQDN and it is fully operational and working (tested with proxies etc..) 
BUT
I get the "Apache2: Could not reliably determine the server's fully qualified domain name..." at apache2 startup.

I don't get how I get that error message and yet the server works perfectly.
I am suspicious of my /etc/hosts file or virtual server set ups.
Here they are:
/etc/hosts:
```

127.0.0.1	localhost
127.0.1.1	ubuntuserver

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

/etc/apache2/sites-available/jameopotato:
```

<VirtualHost *:80>
	ServerAdmin something@something.com
	ServerName jameopotato.com
	ServerAlias www.jameopotato.com
	ServerSignature On
	DocumentRoot /var/www/jameopotato
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/jameopotato>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
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
/etc/apache2/httpd.conf:
```

NameVirtualHost *:80
<VirtualHost *:80>
	ServerAdmin someone@something.com
	ServerName jameopotato.com
	ServerAlias www.jameopotato.com
	DocumentRoot /var/www/jameopotato	
</VirtualHost>


```

---

### Post by JameoPotato on 2008-06-01
fixed it myself.

Had to add, "ServerName FQDN.com" (where FQDN is your fully qualified domain name) to /etc/apache2/apache2.conf
and run "sudo /etc/init.d/apache2 reload"

---

### Post by quelx on 2008-06-01
You have 3 apache virtual servers using the same **ServerName** directive

/etc/apache2/sites-available/jameopotato:
```
<VirtualHost *:80>
	ServerAdmin something@something.com
	ServerName jameopotato.com
	ServerAlias www.jameopotato.com
.

```


/etc/apache2/httpd.conf:
```
NameVirtualHost *:80
<VirtualHost *:80>
	ServerAdmin someone@something.com
	ServerName jameopotato.com
	ServerAlias www.jameopotato.com

```

an you have it now */etc/apache2/apache2.conf* also has the same **ServerName**.  I believe apache only processes the first instance and ignores the rest.

Back to your original question, apache tries to get the FQDN from **hostname -f** which is why apache was complaining because it was returning nothing (and probably still is).

For example I have *example.com*/*[www.example.com](www.example.com)*/*mail.example.com* setup in dns to point to my apache server.  **hostname -f** shows *example.com* I only have **ServerName** directives setup in the virtual hosts for *[www.example.com](www.example.com)* and *mail.example.com*.  If your DNS is setup properly apache will start with any fuss about the server name.

If you don't want to muck aroung with DNS I think you can add a line to your */etc/hosts* file with the ipaddress (not the loopback) followed by the fqdn, eg. **192.168.1.10 jameopotato.com** and apache will be just as happy with out the **ServerName** in */etc/apache2/apache2.conf*

I think you can safely and probably should remove the **ServerName** directive from **apache2.conf** and clean up the conf files (httpd.conf should be empty, Ubuntu uses apache2.conf),  You will avoid problems in the future if you make changes to */etc/apache2/sites-available/jameopotato*.

BTW
I forgot to mention I am using **dnsmasq** for dns when I posted in the **Absolute Beginner** which is why I don't need the **ServerName** option in */etc/apache2/apache2.conf*.  **dnsmasq** reads the */etc/hosts* file and is able to report the fqdn to apache or any other apps that need it. :???:

Hopefully this little bump gets somebody who knows apache better and they jump in.

---

