---
title: "Web development server"
date: 2008-03-15
forum: Server Platforms
---

### Post by mriggen on 2008-03-15
I am trying to set up a LAMP server to use as a simple home web development test server. My idea was to create a setup similar to what I use at work except using ubuntu instead of windows. I looked all over and I couldn't find anything that covered what I'm looking to do. I don't have much experience with linux or setting up a server.

I took a spare computer and installed ubuntu 7.10 server edition. My plan is to develop on my Mac and drop the files on the ubuntu box to serve the pages on the local network only. 

What I want is to be able to type in [http://192.168.1.somenumber/websitefolder/](http://192.168.1.somenumber/websitefolder/) and I will see what I'm working on in the browser. So far I can't even get a default apache page to show.

My home network uses a Linksys router with the standard local ip 192.168.1.1. How would I setup the server so it uses 192.168.1.2 or something like that. After that is taken care of I guess I would need to install samba so I can save files to the server.

I hope that explains it enough. Any help or direction would be greatly appreciated.

---

### Post by freebeer on 2008-03-15
I don't know anything about Macs, but on the linux side you'll probably want to give the Apache machine a static IP address (that way the IP will always be the same).

I run an FTP server as well, and that's how I transfer my files to the server.

---

### Post by mriggen on 2008-03-16
I read a tutorial that said I would need to set a static IP address. The problem is that I'm so new to this kind of thing that I don't know how to set that properly. I played around with the interfaces config file based on what they showed in the tutorial but that didn't work. Basically my question right now is how would I set the static IP address to 192.168.1.2 

Keep in mind this is for the local network only.

This is what my interfaces file currently has that isn't working:

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254

I guess my confusion is understanding what each setting is for.

---

### Post by freebeer on 2008-03-16
What isn't working, exactly.  Off-hand, I don't see anything wrong with those settings (assuming that they are correct).  Can you get on the net?  Or is it that people from outside (the internet side) can't access your server?

---

### Post by TurboRush on 2008-03-17
Are you positive your LAMP server is connected to the network? Are you using wired or wireless?

With linksys routers you can point your browser to 192.168.1.1 and log into the admin pages of the router. There is a tab/screen that will list all the clients connected to the router... that will obviously give you the IP address of the Ubuntu server and validate that your network connection is working.

---

### Post by jonabyte on 2008-03-17
> **mriggen said:**
>  Basically my question right now is how would I set the static IP address to 192.168.1.2 


You will need to check your router and see what number the ips start at.
For example mine starts assigning at 192.168.1.50.
Therefore I can have my server(s) with ips below .50.
Your router could have assigned .2 to your mac.

---

### Post by Joeb454 on 2008-03-17
Usually your router is the one to deal with the IP Address handling. I know I have to go into my router to change whether the IP for a PC on my LAN is dynamic or static :)

Hope that helps :)

---

### Post by mriggen on 2008-03-18
I was able to ping the server from my other computer. But I haven't been able to connect. When you only need to connect locally does it matter what broadcast and gateway are set to? Should they be the same as address? Also, should the router be set to static or should it stay on DHCP.

Sorry, it seems the more I work at it the more questions I get.

I also couldn't find in the router settings where it shows a list of  connected clients. The router is a WRT54G maybe that's a feature in a newer model.

Thanks

---

### Post by Greyfox67 on 2008-03-18
Your IP can stay dynamic if need be: go to [http://www.dyndns.com/](http://www.dyndns.com/) for tools to help you keep your site with a dynamic IP.

To access your router; in a web browser type 192.168.1.1 for access page. Login is usually blank with password as admin - unless you've set it manually to something else. If that's the case try resetting your router. Back of the router small pin hole; hold in a few secs. 

You'll have to place your server in the DMZ so folks can access it outside your network - this can be done through the router access page as well. 

Once all this is done and you access your start web page with apache (apache2 I assume) then there are plenty of resources here to help you get started.

---

### Post by PopsTX on 2008-03-19
mriggen;

Just finished building a second Development Server as you are trying to do.  The newest running Gutsy (41 virtual sites) and the other running Debian Sarge (19 virtual sites).

Both are set up pretty much the same and on the same network:  Both do exactly what you're trying to do and neither are visible to anyone or any machine outside the local network.

The "Trick" is setting up "Ethernet Aliases", which you eluded to.  Then, you will be able to use a regular URL request: [http://192.168.???.???/](http://192.168.???.???/)

I've had to do absolutely NO CONFIGURING to my routers (Netgear).  However, that doesn't mean you can or will escape some tweaking in that department:  Depending on your particular network.

If you have not already discovered:  You must also create a file for each virtual site you wish to create and place it in /etc/apache2/sites-available  Then restart Apache after "Enabling" the sites with a command of "a2ensite SITE_NAME".

The example below is for the "network interfaces": /etc/network/interface
```

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet dhcp
name Ethernet LAN card
broadcast 192.168.0.255
network 192.168.0.0

### Web01
auto eth0:0
iface eth0:0 inet static
name Ethernet LAN card
address 192.168.0.21
netmask 255.255.255.0
broadcast 192.168.0.255
network 192.168.0.0
gateway 192.168.0.1

### Web02
auto eth0:1
iface eth0:1 inet static
name Ethernet LAN card
address 192.168.0.22
netmask 255.255.255.0
broadcast 192.168.0.255
network 192.168.0.0
gateway 192.168.0.1

```

Just continue the schema for each virtual site you plan on creating.

A sample "Sites Available" template is below. This particular file is named web01 and is located in /etc/apache2/sites-available/

```

NameVirtualHost 192.168.0.21
# FILE: /etc/apache2/sites-available/web01
# This is the config file for web1 virtual sever
##
##
##
<VirtualHost 192.168.0.21>
	ServerAdmin YourEmail@SomeMXDomaini.com
	DocumentRoot /home/Your_Folder/www/web01/htdocs
	ServerName KUBUNTU:80
	ServerAlias 192.168.0.21
	<Directory />
		Options FollowSymLinks
		AllowOverride all
	</Directory>
	<Directory "/home/Your_Folder/www/web01/htdocs">
		Options -Indexes FollowSymLinks MultiViews ExecCGI Includes IncludesNOEXEC
		AllowOverride all
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /home/johnhouston/www/web01/htdocs/cgi-bin/
	<Directory "/home/Your_Folder/www/web01/htdocs/cgi-bin">
		AllowOverride all
		Options ExecCGI FollowSymLinks
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /home/Your_Folder/www/web01/logs/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel debug

	CustomLog /home/Your_Folder/www/web01/logs/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options -Indexes MultiViews FollowSymLinks
        AllowOverride all
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
        Allow from 192.168.0.2/255.0.0.0 ::1/128
        Allow from 192.168.0.3/255.0.0.0 ::1/128
        Allow from 192.168.0.4/255.0.0.0 ::1/128
        Allow from 192.168.0.5/255.0.0.0 ::1/128
    </Directory>
</VirtualHost>

```

Both the dev. boxes use pretty much this same configuration and I would almost bet your next paycheck that once you get it set up, you'll never, ever have any problems.

The old Debian box has been running 24/7 for almost three years with the exception of a few power outages and a few hours to replace the fans. the only reason I'm keeping two machines is some of the production sites are on servers using older versions of PHP and MySql.  As time permits, and their budget... They get moved to more "modern" servers.  I keep a mirror of each production site on the dev boxes and this practice has paid off in spades more than once.

---

### Post by mriggen on 2008-03-19
PopsTX,

Thanks, that looks promising. I'll give it a try and see if it solves the problem.

---

