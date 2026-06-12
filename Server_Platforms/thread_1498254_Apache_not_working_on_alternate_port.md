---
title: "Apache not working on alternate port"
date: 2010-05-31
forum: Server Platforms
---

### Post by gnat man on 2010-05-31
I have tried setting apache up on port 8000, because my ISP blocks port 80.

When I try to listen on just port 8000, I can never connect, internally or externally.  When I try to listen on both 8000 and 80, my internal computers will drop the 8000 from the url and connect on 80, and external computers try to do the same thing, but can't get through on port 80.

I know my router is set up correctly, I have 80, 8000, and 8888 all being forwarded, I have confirmed with pcflank.com that 80 is blocked, but 8000 and 8888 are open.  I am able to connect to gnump3d through port 8888 internally and externally, but not apache2 on port 8000.

netstat -tnap confirms that apache is running and listening on ports 80 and 8000 to all users.

So I'm at a loss here for how to fix this, any ideas?

---

### Post by markbahnman on 2010-05-31
What is your default virtual host file set up like in /etc/apache2/sites-enabled (I think it's something like 000-default)?

---

### Post by gnat man on 2010-05-31
I changed only the top line:

```
<VirtualHost *>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
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

I also changed the line in ports.conf to say:

NameVirtualHost *

Let me know if it should be any different.

---

### Post by new_tolinux on 2010-05-31
On my testserver I run my normal website on port 80 and my admin-stuff (phpmyadmin etc.) from port 8181.

The first line in my /etc/apache2/sites-enabled/001-admin is:
```
<Virtualhost *:8181>
```
The same works for my old website which ATM is still running on port 79:
```
<Virtualhost *:79>
```

As far as I can remember I did not change anything else (and I can't find any changes about ports in my /etc/apache2/apache2.conf either)

---

### Post by _Mark_ on 2010-05-31
Port 8000 maybe already in use try 8080 instead

---

### Post by gnat man on 2010-05-31
Good thinking, I know 8080 is in use by something else, so I went with 6000, which I know is free, still no luck.

---

### Post by new_tolinux on 2010-06-01
After editing your config-files, you'll have to restart your webserver-service before testing. Otherwise it won't read the new config-files, so you'll get no results.

```
sudo /etc/init.d/apache2 restart
```

Edit: Also keep in mind that firefox can block certain ports by default.

---

### Post by pwaugh on 2010-06-01
First, the NameVirtualHost doesn't go in the port.conf file, it goes in your httpd.conf or preferably (if you are configuring virtual hosts) in each available hosts conf file located in /etc/apach2/sites-available just above the <VirtualHost > container.

Note, that you need to direct Apache above that to listen to the ports you want it to respond to:

```
Listen 80
Listen 8000
Listen 8080

```
> see: [http://httpd.apache.org/docs/2.2/bind.html](http://httpd.apache.org/docs/2.2/bind.html)

And note that <VirtualHost *> is meaningless!

> See:  [http://httpd.apache.org/docs/2.2/dns-caveats.html](http://httpd.apache.org/docs/2.2/dns-caveats.html)

You must either specify a port (*:port, for name based virtual hosting) or specify an IP (1.2.3.4, for IP based virtual hosting).  If you specify neither, then there would be no virtual host, as you would be saying map any connection from any host on any port here!

So, what you want is something like this:

```
Listen 8080

NameVirtualHost *:8080

<VirtualHost *.8080>
  DocumentRoot    /var/www
  ServerName       www.domain.tld
  ServerAlias      domain.tld, *.domain.tld
  ServerAdmin      admin@localhost
</VirtualHost>
```

where, of course, you replace with your domains and email.

> see:  [http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)

Remember to restart apache!

```

sudo /etc/init.d/apache2 restart

```

patrick

---

### Post by pwaugh on 2010-06-01
Oh yeah, if this is your only host, then you can just edit the one file:

```

~$ sudo gedit /etc/apache2/sites-available/default

```

But, if you are creating a 'new' virtual host, and then you will need to create a new file in that same directory with any name you choose, and then you'll need to "enable" it like so:

```

~$ sudo a2ensite filename_you_created

OR

~$ sudo ln -s /etc/apache2/sites-available/filename /etc/apache2/sites-enabled/.

```

But remember after either:

```

~$ sudo /etc/init.d/apache2 reload

```

patrick

---

### Post by gnat man on 2010-06-01
Thank you for the advice, but I still can't get it to work.  When I run on port 80, I can connect just fine locally, but nothing works from anywhere on any other port.  Here are my conf files, if you could look over them real quick and see if you spot any stupid errors, it would be much appreciated.

/etc/apache2/sites-available/default
```
<VirtualHost *:6000>
	ServerAdmin gnatman@gnatopia.com
        ServerName       www.gnatopia.com
        ServerAlias      gnatopia.com, *.gnatopia.com
	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
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

and /ect/apache2/ports.conf

```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:6000
Listen 80
Listen 6000
Listen 8000
Listen 8080


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

Thanks for all the attempts at help. (I am restarting apache after every conf change BTW.)  I also mostly use chrome, but I have also tried firefox with no luck to connect.

---

### Post by pwaugh on 2010-06-01
Did you setup port forwarding on your cable modem/router?

If you are behind a NAT router (ie on say a cable modem) then it is assigned your external IP by your ISP.  When a request comes into it on port 80 (or whatever) unless the port is forwarded to your web server which is on an unroutable IP like 192.168.1.100, then it will just let the packet die.  You need to login to your router and forward TCP port 80 requests to your internal web server on whatever IP it is on.

---

### Post by gnat man on 2010-06-02
I have double and triple checked my router configuration, and port 8888 works for gnupm3d, so I know that's working great.  Even internally, using the internal IP address, even using localhost, I can't connect to an alternate port.

With the configuration listed above, I can connect to [http://localhost](http://localhost), and [http://192.168.1.100](http://192.168.1.100) from another internal machine but not localhost:6000 and not localhost:8000 and not 192.168.1.100:6000, etc.

---

### Post by pwaugh on 2010-06-02
Be sure to clear your FireFox cache too, I ran into that one time.

First, it seems like probably should just focus on getting the virtual host you want up and running internally.

Could you describe your topology a bit?  What IP (internally) is stuff on, and what host names are you using?  

Then post (from the web server):

/etc/hosts
/etc/apache2/apache2.conf
/etc/apache2/httpd.conf
/etc/apache2/ports.conf
/etc/apache2/sites-available/default     (Is this the ONLY file in this directory?)

Can you post the directory listing of /etc/apache2/sites-enabled?

Can you confirm your external IP is:  74.192.10.159?

I'm confused from your prior posts, how many web servers (virtual hosts) are you trying to run?  What host, name and ports do you want them on?

Sorry, but I'm pretty new at this too, and so I'm not good at guessing what you are wanting to do.  But, first focus on getting it working internally.

Can you detail the port forwards you have setup?  Can you post the output that you think confirms (internally) that the ports are there, open and responding?

Once all this is in one place, and you have the agreed initial goal of getting x,y, & z to work internally, then once that's up you can then worry about the Internet side.

I'll shut up now.  :)

patrick

---

### Post by gnat man on 2010-06-03
I appreciate the help from everybody, but I decided to go with an alternate solution.  I switched ISPs, and now I don't have anymore problems.

Thanks.

---

### Post by new_tolinux on 2010-06-03
> **gnat man said:**
> I appreciate the help from everybody, but I decided to go with an alternate solution.  I switched ISPs, and now I don't have anymore problems.

Thanks.
Maybe you could mark this thread solved, since the original problem (the webserver being reachable from the outside world) is solved.

---

