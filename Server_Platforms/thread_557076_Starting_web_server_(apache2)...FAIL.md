---
title: "* Starting web server (apache2)...FAIL"
date: 2007-09-22
forum: Server Platforms
---

### Post by bronzemonkey on 2007-09-22
Until yesterday I had a working web server (for testing) with 4 vhosts. The only issue was that I was getting errors at boot about mixing * and non-* ports. When I carried out the changes someone here recommended, my web server failed to start, and still failed to start when I reversed the changes.

Now I have gotten to the point where I simply get this message:

*** Starting web server (apache2)...[fail]**

Nothing else whatsoever. How can I get my webserver back up and running?

---

### Post by MJN on 2007-09-22
Check (and post) the logs... They should always be your first port of call really.

Mathew

---

### Post by bronzemonkey on 2007-09-22
Which logs? Apache2's error.log ends with "Unable to open logs" and it has been that way since the web server has failed to start.

---

### Post by MJN on 2007-09-22
That's probably indicitive of the problem. Post the output of **ls -l /var/log/apache2** (I think that's the default Apache log area - it's been a long time since I set mine up) and also run **sudo apache2ctl configtest**

Incidentally, you are running **/etc/init.d/apache2** **start** with sudo (or as root)? (just checking - not doing so when required can often throw up unexpected and non-meaningful errors)

Your virtualhost config files might also be useful (I know I'm asking for a lot, but we need evidence to find the cause).

Mathew

---

### Post by bronzemonkey on 2007-09-22
I should also add that attempts to ping [www.google.com](www.google.com) produce the message "connect: Network is unreachable".

This is all pretty annoying because everything was working until I followed another member's instructions to overcome some error messages.

> **MJN said:**
> Post the output of **ls -l /var/log/apache2**

total36
-rw-r----- 1 root adm 14462 2007-09-21 17:30 access.log
-rw-r----- 1 root adm 17645 2007-09-22 14:29 error.log

> **MJN said:**
> also run **sudo apache2ctl configtest**

Syntax OK

> **MJN said:**
> Incidentally, you are running **/etc/init.d/apache2** **start** with sudo (or as root)?

Yes. The error appears when my server boots up and reappears every time I try to start apache.

> **MJN said:**
> Your virtualhost config files might also be useful

All my vhost .conf files (in /sites-available/ and /sites-enabled) are like this:

<VirtualHost *>
DocumentRoot /home/administrator/domain.com/public_html
ServerName domain.com
<Directory "/home/administrator/domain.com/public_html">
allow from all
Options +Indexes
</Directory>
ErrorLog /home/administrator/domain.com/log
LogLevel warn
</VirtualHost>

**And the default in the /sites-available/ looks like this:**

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

**My router's IP is 10.0.0.0 and the contents of /etc/network/interfaces is below.**

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 10.0.0.20
        netmask 255.0.0.0
        broadcast 10.255.255.255

Let me know if you want the output/contents of anything else.

I have also tried to start again with a fresh install of the server (I am using virtualization software), following my previous steps exactly, but now even this fresh install tells me the network is unreachable as soon as I modify the network/interfaces file. Perhaps this indicates something, but I am totally stumpted and really wishing I had just kept my server with the port error messages...at least it worked then. Thank for help you can provide.

---

### Post by MJN on 2007-09-22
Try commenting out your Errorlog statement(s) and posting the contents of them if there's anything in them (I suspect there isn't if this is what the error is referring to). Incidentally, if you don't copy-and-paste config files verbatim then we cannot omit typos as being a potential cause... and these are extremely common and hence it can be very frustrating to find that's the problem after endless troubleshooting by all!

The network issues are something else - one step at a time!

Mathew

---

### Post by bronzemonkey on 2007-09-22
Seems the problem was that the Errorlog statements failed to specify a file. I simply changed them all to include /error.log at the end and now apache is starting properly.

No apparent problem with the network anymore. It could have been a problem with having 2 virtual machines (but not running at the same time) using the same virtual network adaptor. Not really sure, but seems ok now that I removed the other VM from that host interface. Thanks for your help, really appreciate it!

---

