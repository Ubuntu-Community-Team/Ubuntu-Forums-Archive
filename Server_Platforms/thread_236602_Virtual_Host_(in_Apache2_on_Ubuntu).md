---
title: "Virtual Host? (in Apache2 on Ubuntu)"
date: 2006-08-15
forum: Server Platforms
---

### Post by jms1989 on 2006-08-15
Can you help me with this? 
```
 * Forcing reload of apache 2.0 web server... 
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Mon Aug 14 23:42:37 2006] [warn] NameVirtualHost 127.0.0.1:0 has no VirtualHosts
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Mon Aug 14 23:42:38 2006] [warn] NameVirtualHost 127.0.0.1:0 has no VirtualHosts
                                                                                                       [ ok ]
```

When I restart my Apache2 server I get this, How can I fix it without messing it up?

I'm using Ubuntu Linux, 2.8GHz processer, 439MB of system memory, 40GB Hard Drive.

---

### Post by jms1989 on 2006-08-15
Here is my current file for "/etc/apache2/sites-enabled/000-default" file.

[http://jms-bin.pastebin.ca/132269](http://jms-bin.pastebin.ca/132269)

---

### Post by chrisfay on 2006-08-15
You need to add:

ServerName "www.domainname.tld"   (replacing "www.domainname.tld" with your domain name)

into your apaceh2.conf file...you can put it right under your ServerRoot "/server/root" directive

Are you using virtual hosts or not? If not, comment out:

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/[^.#]*

to:

# Include the virtual host configurations:
#Include /etc/apache2/sites-enabled/[^.#]*

---

### Post by jms1989 on 2006-08-15
I am using virtual hosts, you can view my link in my 2nd post for the settings. I added the ServerName to my apache2.conf.

Now when I restart the server, I get;

```
 * Forcing reload of apache 2.0 web server... 
[Tue Aug 15 04:34:28 2006] [warn] NameVirtualHost 127.0.0.1:0 has no VirtualHosts
[Tue Aug 15 04:34:28 2006] [warn] NameVirtualHost *:8080 has no VirtualHosts
[Tue Aug 15 04:34:28 2006] [warn] NameVirtualHost *:80 has no VirtualHosts
[Tue Aug 15 04:34:29 2006] [warn] NameVirtualHost 127.0.0.1:0 has no VirtualHosts
[Tue Aug 15 04:34:29 2006] [warn] NameVirtualHost *:8080 has no VirtualHosts
[Tue Aug 15 04:34:29 2006] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                                                                 [ ok ]
```

What do I do about the warnings?

---

### Post by chrisfay on 2006-08-15
Port specifications don't go in sites-enabled/000-deafult. They go in ports.conf. The only thing that goes in sites-enabled is virtual hosts.

Your virtual host specifications in your 000-default file are missing info. 000-default should look similar to this:

<VirtualHost *>
DocumentRoot "/var/www/domainname"
ServerName domainname.tld
ServerAlias [www.domainname.tld](www.domainname.tld)
<Directory "/var/www/domainname">
allow from all
Options -Indexes
</Directory>
ServerAdmin [email]admin@domainname.tld[/email]
</VirtualHost>

(replacing domainname and domainname.tld with your domain name info)

Find your apache2.conf file and make sure you have configured it to look for ports in ports.conf file...that area of your pache2.conf should look like:

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

[B]# Include ports listing
Include /etc/apache2/ports.conf[/B]

# Include generic snippets of statements
Include /etc/apache2/conf.d/[^.#]*

---

### Post by jms1989 on 2006-08-15
I updated the 000-default file like you said. Link: [http://jms-bin.pastebin.ca/133738](http://jms-bin.pastebin.ca/133738)

My ports.conf has; Listen 80 and Listen 8080. 

the apache2.conf contains; 
# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

# Include generic snippets of statements
Include /etc/apache2/conf.d/[^.#]*
Reply With Quote

Now when I restart Apache2 I get ```
 * Forcing reload of apache 2.0 web server... 
[Tue Aug 15 21:29:07 2006] [warn] NameVirtualHost 127.0.0.1:0 has no VirtualHosts
[Tue Aug 15 21:29:07 2006] [warn] NameVirtualHost *:8080 has no VirtualHosts
[Tue Aug 15 21:29:07 2006] [warn] NameVirtualHost *:80 has no VirtualHosts
[Tue Aug 15 21:29:08 2006] [warn] NameVirtualHost 127.0.0.1:0 has no VirtualHosts
[Tue Aug 15 21:29:08 2006] [warn] NameVirtualHost *:8080 has no VirtualHosts
[Tue Aug 15 21:29:08 2006] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                                                       [ ok ]
```

When I try to access localhost, It tells me that I don't have permission to access it.

---

### Post by LordHunter317 on 2006-08-15
Please stop using pastebin and include the file here.

Anyway, this is likely a name issue.  Whatever name you're putting in for the virtual hosts, Apache cannot resolve.  If this is for development, add them to /etc/hosts.  If it's for production, fix your DNS.

---

### Post by jms1989 on 2006-08-16
How would I do that? I dont have a /etc/hosts nor do I know to fix my DNS.

I am also behind a router, and I just want it privite for testing. Ok, maby sometimes public, may I ask how to make it public?

EDIT: I forgot to add this.

My computer had problems and I had to restore from a backup. So, I got my orig 000-default file back and I added some more hosts to it.

```
Here is the file; /etc/apache2/sites-enabled/000-default

NameVirtualHost *:78
NameVirtualHost *:8080
#NameVirtualHost 127.0.0.1:0
<VirtualHost *:78>
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
        Allow from all
    </Directory>

</VirtualHost>

<VirtualHost *:8080>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/michaels-web.com
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/michaels-web.com/>
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
        Allow from all
    </Directory>

</VirtualHost>

#<VirtualHost 127.0.0.1:0>
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
        Allow from all
    </Directory>

#</VirtualHost>


#127.0.0.0/255.0.0.0 ::1/128
```

Now when I restart my apache2 server, I get,

 * Forcing reload of apache 2.0 web server... 
[Wed Aug 16 00:03:39 2006] [warn] NameVirtualHost 127.0.0.1:0 has no VirtualHosts
[Wed Aug 16 00:03:40 2006] [warn] NameVirtualHost 127.0.0.1:0 has no VirtualHosts
                                                                                                                                                    [ ok ]

How would I correct this problem?

---

### Post by LordHunter317 on 2006-08-16
You most definitely have /etc/hosts.

---

### Post by jms1989 on 2006-08-16
> **LordHunter317 said:**
> You most definitely have /etc/hosts.

I don't want to argue but, I don't have it. I'll post a pic if you don't beleve me.

---

### Post by LordHunter317 on 2006-08-16
If you don't have it then you totally messed up your install, to the point of probably needing a reinstall.  It's a fundamental file central to DNS resolution.

---

### Post by jms1989 on 2006-08-16
My computer is a desktop, I only need it for testing and privite viewing. I don't need DNS for my computer. Anywho, I'm done checking this thread, I think my server is running ok.

Are you familar with php-fusion? I keep getting a blank page when I go to localhost:8080, that is the address for it.

---

### Post by LordHunter317 on 2006-08-16
> **jms1989 said:**
> I don't need DNS for my computer.Use the Internet or software intended to be used on the Internet?  You need working DNS.

Tons of things depend on the resolver being sane even if DNS is unavaiable.

> Anywho, I'm done checking this thread, I think my server is running ok.No, if /etc/hosts is missing then it's toally messed up.  When I said a reinstall I was totally serious with damn good cause.  Reinstall the box FFS and listen to those trying to give you help.

---

### Post by cptnapalm on 2006-08-17
I'm going to say this:  /etc/hosts is essential.

Your own computer cannot tell that it is localhost without it.

It is that important.

---

