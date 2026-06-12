---
title: "Last step"
date: 2006-07-30
forum: Server Platforms
---

### Post by sdmike on 2006-07-30
Ok So I setup my server on my windows machine using apache2.

Now when I use apache2 on ubuntu using Dapper I'm a little lost on what to do on this part of the code as far as where I put my IP with the port I forwarded and my email?

[COLOR="Red"]NameVirtualHost *
<VirtualHost *>
	ServerAdmin [email]focushacker@gmail.com[/email]
	
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
[/COLOR]

---

### Post by califdon on 2006-07-30
Looks to me like you're all done.  If you're only hosting a single domain name and IP address, that should do it.  It gets more complicated if you have multiple IP addresses and/or multiple domain names.  Whatever HTTP requests arrive at Port 80 will be serviced by Apache at the DocumentRoot /var/www (where you must be sure you have a file "index.html"!).  That's what the wild card * means in the VirtualHost directive.

You mentioned email?  Apache, of course, is not an email server, so if you're talking about sending and receiving email, you need to set up Postfix or some other MTA.

Hope this helps.

---

### Post by sdmike on 2006-07-30
I think you miss understood me. I'm not sure about were I should put my ip at? Like on my windows machine using apache I would put something like 123.56.78.145:8080.

I can't use port 80 because my ISP blocks it.

---

### Post by az on 2006-07-30
/etc/apache2/ports.conf

---

### Post by sdmike on 2006-08-01
Ok so let me get this straight. When I change the ports with my DNS name and change Apache to listen to my port 8080. It will then be able to be accessed on the internet?

And this can all be done in the portconf file?

I wish there was a very clear tutorial on just how to do webpage with apache2. I mean I did one with Apache2 on windows but the linux version is a bit different when it comes to configuring. But it is fun stuff though.
:^o

---

### Post by sdmike on 2006-08-07
Can someone give me an example here if I'm using port 8080 on my ipaddress for the site. Where would I put this is into Apache2 and can someone give me an example. I put port 8080 in ports.conf but that didn't do the trick so I'm stuck for now.

---

### Post by sdmike on 2006-08-07
In the port.conf file I put port 8080 and now apache2 won't start. So what is up here.

I mean in the apache2 in windows I just put my ip with the port I opened and it worked. So all I wonna know is where do I put that into apache2 in linux with an example because I can't find one.

---

### Post by az on 2006-08-07
> **sdmike said:**
> In the port.conf file I put port 8080 and now apache2 won't start. So what is up here.


Is something else using port 8080?  What error do you get?

All you have to do is change that to 8080 and restart (force reload) apache2 and you are using port 8080.

---

### Post by sdmike on 2006-08-08
Nothing else is using port 8080

but here is the error message I got when I rebooted.

[COLOR="Red"]jack@jack-desktop:~$ apache2ctl start
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(98)Address already in use: make_sock: could not bind to address [::]:8080
no listening sockets available, shutting down
Unable to open logs
jack@jack-desktop:~$
[/COLOR]

---

### Post by sdmike on 2006-08-10
Ok well then I will just ask this simple question because I there must be some little thing I'm missing here. My question is where can I find a simple tutorial with examples of the code on how to setup a webserver so I can host my own website?

---

### Post by sdmike on 2006-08-14
Went to Barnes and noble and still couldn't find one. Anyone know where?

---

### Post by chrisfay on 2006-08-14
The error you get sounds like another device is using port 8080. You might try switching to some other random port to verify that apache works. Otherwise, you might try uninstalling and reinstalling apache completely. 

To fix the:

apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

All you need to do is add:

ServerName "www.domainname.tld" (replacing "domainname.tld" with your domain)

to your apache2.conf file

---

### Post by inthewayboy on 2006-08-14
booya:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Towards the end it talks about ports.conf...I used it to see what I needed to install and works very well.

---

