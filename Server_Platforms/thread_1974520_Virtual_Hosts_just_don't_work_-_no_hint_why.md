---
title: "Virtual Hosts just don't work - no hint why"
date: 2012-05-06
forum: Server Platforms
---

### Post by shredding on 2012-05-06
Hey y'all,

I'm new to ubuntu and to some degree new to apache and am trying to configure a virtual host.

I've done approximately 10 tutorials on the topic, each was slightly different - I just don't get it up and running.

The frustrating thing is, that apache throws no errors, no warning, nothing. It's just not working and after hours of trying I've finally given up.

This is what i got now:

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
        ServerName project.localhost
	ServerAlias project.de.localhost
	DocumentRoot /home/chris/www/project/web
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /home/chris/www/project/web/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
```

This resides in a file named "project" in /etc/apache2/sites-available/project. I have sucessfully run a2ensite project, it's available in sites-enabled, I have reloaded and restarted - everything without errors. I have cleared browsercache.

From my understanding my project should now be available at [http://guidr.localhost](http://guidr.localhost) - but it isn't. I tried editing /etc/hosts without success.

I would really appreciate if someone could have a look into this. I'm really down to my last, and I would really like to know how I can make apache tell me, whats wrong.

---

### Post by volkswagner on 2012-05-06
You say 
>  [http://guidr.localhost](http://guidr.localhost) - but it isn't. I tried editing /etc/hosts without success.


Yet your vhost file has servername as project.localhost.

Please post your /etc/hosts file.

What happens when you enter [http://project.localhost?](http://project.localhost?)

---

### Post by shredding on 2012-05-06
> **volkswagner said:**
> You say 


Yet your vhost file has servername as project.localhost.

Please post your /etc/hosts file.

What happens when you enter [http://project.localhost?](http://project.localhost?)

Sorry, guidr is the real name, I just changed it to project to make it clear.

This is my (unedited) hosts file:

```
127.0.0.1	localhost.localdomain	localhost
::1	Chris-Kubuntu	localhost6.localdomain6	localhost6
127.0.1.1	Chris-Kubuntu

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Thanks for your help!

---

### Post by SeijiSensei on 2012-05-06
For name-based virtual hosting to work, the URL must contain one of these

```

ServerName project.localhost
ServerAlias project.de.localhost

```

That's how Apache knows which vhost definition to use.  If you're trying to connect to this host from the server itself over the localhost interface, modify your /etc/hosts file (as root with sudo) like this:

```
127.0.0.1	localhost.localdomain	localhost [color=blue]project.localhost project.de.localhost[/color]
```

Then use the URL [http://project.localhost/](http://project.localhost/).

If you're trying to connect over the network, the client machine needs to have these entries in its hosts file with the network IP of the server instead:

```
10.10.10.10 project.localhost project.de.localhost
```

---

### Post by shredding on 2012-05-08
Thank you very much for your answer and your efforts!

I'll try directly this evening and report back!

---

### Post by shredding on 2012-05-08
Hey, this did the trick somehow: project.localhost is now callable in my browser, but it points to the same directory as localhost (which makes the whole thing somewhat pointless).

I'm really wondering why, because I have changed the DocumentRoot, my guess is, that it's still not connected with my sites-available/project ...

What's really driving me crazy is not that it's not working, it's that I don't understand whats going on.

HOSTS:
```
127.0.0.1	localhost.localdomain	localhost project.localhost project.de.localhost
::1	Chris-Kubuntu	localhost6.localdomain6	localhost6
127.0.1.1	Chris-Kubuntu

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

PORTS.CONF
```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
# NameVirtualHost *
Listen 127.0.0.1:80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>


```

SITES-AVAILABLE/PROJECT (I have reloaded and restarted apache)
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
    ServerName project.localhost
	ServerAlias project.de.localhost
	DocumentRoot /home/chris/www/project/web
	<Directory /home/chris/www/project/web/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>

```

---

### Post by volkswagner on 2012-05-08
Have you enabled the site project?  If so It should be listed in /etc/apache2/sites-enabled.

```
ls -alt /etc/apache2/sites-enabled
```

Also in ports.conf, you don't need to specify the address.  I'd change the listen directive to:

```
Listen 80

```


Also do you have anything in /etc/apache2/httpd.conf?

```
less /etc/apache2/httpd.conf
```

---

### Post by shredding on 2012-05-09
Thank you!

That finally did it! I did do a2ensite guidr (which I swear I did before), but it appeared I had not done it with sudo. Now everything works.

Thank you again!

Would you mind telling a few words about this *Listen 80* directive? As I understand it, it's the IP adress and now it listens to 127.0.01 (localhost) and Port 80.

---

### Post by volkswagner on 2012-05-09
> **shredding said:**
> 

Would you mind telling a few words about this *Listen 80* directive? As I understand it, it's the IP adress and now it listens to 127.0.01 (localhost) and Port 80.

I'm not 100% sure, but I believe using the loopback (127.0.0.1) will limit Apache to serving the local machine.  If other lan connected machines try to access it, they may be denied access????

Specifying the address may also be helpful for machines with multiple interfaces to direct traffic.

---

### Post by CharlesA on 2012-05-09
> **shredding said:**
> 
Would you mind telling a few words about this *Listen 80* directive? As I understand it, it's the IP adress and now it listens to 127.0.01 (localhost) and Port 80.

It tells what IP or port to listen for that domain name on.

---

### Post by SeijiSensei on 2012-05-09
If you specify 

```
Listen 127.0.0.1:80
```

then Apache will only serve requests it receives via the localhost interface.  In particular, if the machine is connected to a network, it will ignore HTTP requests that arrive on any network interfaces like eth0.  To make Apache listen on all interfaces use

```
Listen 80
```

The port number, 80, is the standard for HTTP.  You can see a list of all the standard port assignments (those numbered from 0-1023) and many nonstandard assignments by looking at the file /etc/services.

---

