---
title: "Setting up Apache - beginner problems"
date: 2011-02-12
forum: Server Platforms
---

### Post by vacco on 2011-02-12
I am trying to set up my system with apache to host a website or two. I am able to get the "It works" page up and running, but no matter what I do, I am not able to change it.

I have configured the system with a static IP address on the home network, and configured my router to forward port 80 to this IP.

The default install of Apache comes with an index.html saying "It works" in the /var/www directory. I was able to access this both on my local network and from the internet.

I then tried to make a modification to /var/www/index.html. The change is visible when I enter the site by typing localhost, hostname or the internal IP address in my browser address field, but if I enter the global IP or one of the domains (dyndns and .tk) I connected to it, I get the original version. Only if I type ipaddress/index.html (or similarly domain.com/index.html) will I see the modified version.

This is /etc/apache2/sites-enabled/000-default (which was placed there by the default install): ```
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
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

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

### Post by hawkmage on 2011-02-12
In the directory section of your VirtualHost has:
```
Order deny,allow
Deny from all
Allow from 127.0.0.0/255.0.0.0 ::1/128
```You are allowing access to this virtual host from localhost.

You may want to change it to:
```
Order allow,deny
Allow from all
```

---

### Post by vacco on 2011-02-12
Still no luck :(

---

### Post by hawkmage on 2011-02-12
OK do you have a firewall enabled?

---

### Post by volkswagner on 2011-02-13
It is either browser cache, you may need to refresh the browser to see the changes, or it could be a permission issue with index.html.

---

### Post by vacco on 2011-02-13
OK, it is working now after restarting my computer (which is weird since I did in fact run "sudo /etc/init.d/apache2 restart").
The problem now is that I have configured two virtual hosts, and one of them is not working properly.

If I enter via my global IP I see the modified version of the default Apache page (/var/www/index.html), which makes sense.

If I enter via domainone.dyndns.org I see index.html of the site configured to respond to this address.

BUT: if I enter domaintwo.tk, I still get the modified default page in /var/www, even if I specifically enter domaintwo.tk/index.html.


Both sites are configured identically as far as I know, with the only difference being ServerName and DocumentRoot.

/etc/apache2/sites-available/domainone:
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName domainone.dyndns.org

	DocumentRoot /var/www/domainone
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

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Allow from all
    </Directory>

</VirtualHost>
```

/etc/apache2/sites-available/domaintwo:
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName domaintwo.tk

	DocumentRoot /var/www/domaintwo
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

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Allow from all
    </Directory>

</VirtualHost>
```

There are links to both in sites-enabled created with a2ensite.
Note: these are not the actual domain names I use, but is used in an identical context. The domains they are part of are correct (.tk and .dyndns.org)

---

### Post by vacco on 2011-02-13
I just tried copying the configuration file for domainone, rename the copy domaintwo and change ServerName and Documentroot to make sure they are otherwise identical, but still no change.

---

### Post by CharlesA on 2011-02-13
Are you accessing this site from inside or outside of the local network?

---

### Post by vacco on 2011-02-13
Inside. The same machine that is hosting the sites to be precise.

---

### Post by CharlesA on 2011-02-13
Is there an entry in DNS or in the hosts file to point a certain domain name to the ip address of the machine in particular?

---

### Post by vacco on 2011-02-13
I have not done anything with the files you mentioned. I have my router configured to forward port 80 to the machine where I am hosting this. Both domains point to my global IP, and with virtual hosts configured as previously posted.

I am suspecting .tk might have a simple DNS system where the domain is translated to the IP in such a way that Apache thinks the user accessed the server by typing the IP rather than the URL in the address bar.

---

### Post by CharlesA on 2011-02-13
Try adding the .tk domain to your /etc/hosts file and see if it resolves correctly.

That would rule out a DNS problem.

---

### Post by vacco on 2011-02-13
This is my /etc/hosts file:
```
192.168.2.222	lacieubuntu	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
::1	lacieubuntu	localhost6.localdomain6	localhost6
127.0.1.1	lacieubuntu

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

I am not quite sure where to add the .tk domain or how the syntax should be.

---

### Post by CharlesA on 2011-02-13
Throw it in like this:

```
192.168.1.1     somedomain.tk

```

Where 192.168.1.1 is the IP address of the server hosting the site.

---

### Post by vacco on 2011-02-13
Thank you! Things are looking good for the moment. As a last question: how should I restart Apache after making a change to a virtual host config file? I have been trying "sudo /etc/init.d/apache2 restart" quite a few times, but I always have to reboot to make changes work, and  am honestly getting a little bit tired of that :confused:

---

### Post by CharlesA on 2011-02-13
Easy:

```
sudo service apache2 restart
```

If it's working with an entry in the hosts file, then it's more then likely a DNS problem.

Could try accessing the site from outside your local network and see if it's working as expected or not.

---

