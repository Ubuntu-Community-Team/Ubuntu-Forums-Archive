---
title: "Can't install LAMP server on Ubuntu"
date: 2008-09-18
forum: Server Platforms
---

### Post by Epifrin on 2008-09-18
So I have installed Ubuntu a couple days ago, and setup the Xampp package, but was unable to get any web pages -apart from included in Xampp- to display on localhost, because of some permission issue.

Then I found a detailed _[guide on how to set LAMP on Ubuntu](http://groups.drupal.org/node/6266)_, so I stopped Xampp & deleted it from the folder /opt. I followed all of the guide's steps but problems persist. I get this error message when I type in the address bar "localhost", even though I don't use Xampp anymore:

404 Not Found
The requested URL /xampp/ was not found on this server.

My question is, how do I display localhost and make sure that my local server installation has been successful? Thanks alot in advance.

---

### Post by cariboo on 2008-09-18
You have to change the document root in /etc/apache2/sites-available/default to:

```
DocumentRoot /var/www
```

Jim```

```

---

### Post by Epifrin on 2008-09-19
Thanks, but I'm afraid my "default" file already includes the code you posted. Here it is:

```
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

Also, I was required during the installation to create a file "localhost" in the same folder that contains "default". Dunno if it could be of any interference but here is its code anyway:

```
# Based on Drubuntu multisite config file from http://groups.drupal.org/node/6266
#
# IMPORTANT!  READ ME!
# In the VirtualDocumentRoot below, change USER to match YOUR USERNAME
#
# What this file does:
# Configure Apache so that when you browse the local URL http://DOMAIN.localhost/
# Apache will use the siteroot path /home/USER/workspace/DOMAIN/
# Remember to add your new DOMAIN.localhost domain to /etc/hosts for 127.0.0.1

<VirtualHost *>
        ServerName localhost
        ServerAlias localhost *.localhost
        VirtualDocumentRoot /home/fouad/workspace/%1/
</VirtualHost>
```

I'm all confused as I still get this error message when entering "localhost":

Not Found
The requested URL / was not found on this server.
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch Server at localhost Port 80

Any help is greatly appreciated.

---

### Post by cariboo on 2008-09-20
I've never had to set up localhost as a virtual server. I haven't installed Drupal lately, but, that doesn't look right to me. Have you tried access your web page using your computers ip address eg:

```
http://192.168.1.200
```

Of course you would have to change the ip address to your computer's ip address.

Jim

---

### Post by windependence on 2008-09-20
> **Epifrin said:**
> So I have installed Ubuntu a couple days ago, and setup the Xampp package, but was unable to get any web pages -apart from included in Xampp- to display on localhost, because of some permission issue.

Then I found a detailed _[guide on how to set LAMP on Ubuntu](http://groups.drupal.org/node/6266)_, so I stopped Xampp & deleted it from the folder /opt. I followed all of the guide's steps but problems persist. I get this error message when I type in the address bar "localhost", even though I don't use Xampp anymore:

404 Not Found
The requested URL /xampp/ was not found on this server.

My question is, how do I display localhost and make sure that my local server installation has been successful? Thanks alot in advance.


Just deleting the application folder does not remove the application.

How did you install xampp? Did you use apt-get? Or compile from source?

If you installed from packages using apt-get then you need to do this:

```
sudo apt-get remove xampp
```

-Tim

---

### Post by Spiny Norman on 2008-09-20
My suggestion is to start again use the procedure at [http://www.howtoforge.com/perfect_setup_ubuntu_6.06]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06")
You will need to modify that slightly for 8.04, e.g. no need to vi the apache 2 config file. Also do not put the ethernet cable in immediately, let the system fail to set up DHCP then use the manual option. Put the cable in before you do the update. Most other things apply.

---

### Post by Iowan on 2008-09-20
The [ 8.04 Perfect Server]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts") version.
A [minimal]("http://www.howtoforge.com/minimal-ubuntu-8.04-server-install") server setup.

---

