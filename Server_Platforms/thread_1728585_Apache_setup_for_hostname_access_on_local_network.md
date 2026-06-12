---
title: "Apache setup for hostname access on local network"
date: 2011-04-13
forum: Server Platforms
---

### Post by gwilym on 2011-04-13
Hi,

I have installed Ubuntu on four machines at work and have been blown away - people love it !

On my machine I have Apache setup for web development and other machines can "see" it using my IP address. I would like to have it so they can access by the name of my computer though. I have no local DNS server so I guess I need to hard code the relationship in each machine?

Ideally I'd actually like to be able to use subdomains (which I use locally to avoid annoying .htaccess path problems). i.e. from another machine on the network to go to;

[http://application.mymachine/](http://application.mymachine/)

Any ideas appreciated...

---

### Post by fenderr357 on 2011-04-14
So first you will need to create a host file in "/etc/apache2/sites-available/". But you can always just edit the default one. It should basically look like this:

```

#/etc/apache2/sites-available/default
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
</VirtualHost>
```So to name your site, just edit it like this (Im using local IP's for example, you can leave it as "*"):

```

#/etc/apache2/sites-available/default
<VirtualHost 192.168.20.10:80>
    
    ServerAdmin webmaster@localhost
    ServerName application.mymachine #or whatever
    
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

</VirtualHost>
```Then enable the site with a2ensite.

After that, since you have absolutely no DNS, you will have to hardcode the relationships in each machines DNS hosts file (including the server). Keep in mind though, that even a simple home router usually handles DNS, so you may not have to.

---

### Post by gwilym on 2011-04-28
Thanks for the reply!

Sooooo ... I have the following in my default. Does that mean when I go to my IP from another machine I should be pointed to "/www/councils" - at the moment it points me to my document root.. "/www/" ...

```
<VirtualHost 192.168.1.200:80>
	ServerAdmin webmaster@localhost
	ServerName councils.gwilym-desktop
	
	DocumentRoot /var/www/councils
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/councils>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
```

---

### Post by volkswagner on 2011-04-28
```
<VirtualHost 192.168.1.200:80>
	ServerAdmin webmaster@localhost
	ServerName councils.gwilym-desktop
	
	DocumentRoot /var/www/councils
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/councils>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
```

With the above you should have [http://192.168.1.200](http://192.168.1.200) directed to /var/www/councils.  After making the change did you restart apache2?

```
sudo /etc/init.d/apache2 reload
```

You will want to create a new virtual host file like above by copying it then editing the copy.  You can create a new subdomain for each application in each host file.

Then for other machines on the LAN you can edit their host file to include

```
192.168.1.200 councils.gwilym-desktop
192.168.1.200 *.gwilym-desktop
```

Some [valuable reading]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html") for Name based virtual hosting.

---

