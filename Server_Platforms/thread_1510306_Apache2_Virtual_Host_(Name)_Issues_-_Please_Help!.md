---
title: "Apache2 Virtual Host (Name) Issues - Please Help!"
date: 2010-06-15
forum: Server Platforms
---

### Post by eric_1982 on 2010-06-15
I am really struggling getting Virtual Host to work correctly on Ubuntu 10.04. I had no issues with 9.10 but am just having no luck after upgrading. I keep getting the following message when restarting apache. 

[Tue Jun 15 09:50:56 2010] [warn] VirtualHost site2:0 overlaps with VirtualHost site3:0, the first has precedence, perhaps you need a NameVirtualHost directive
[Tue Jun 15 09:50:56 2010] [warn] NameVirtualHost *:80 has no VirtualHosts

It keeps on defaulting all web request to the root folder /var/www/.

I am looking on getting 3 sites working. One that defaults to the root dir /var/www, and site2 and site3 in there own folders inside /var/www/. Example: /var/www/site2 and /var/www/site3.

I have create a file called site2 and site3 in /etc/apache2/sites-available and have done a sudo a2ensite site2 and sudo a2ensite site3. After doing this I have done and /etc/init.d/apache2 reload. 

Listed below is what my two site config files look like. I also have the default config file with no modifications to it as well. 

site2:

<VirtualHost site2>
	ServerAdmin [email]tec@testserver.123.com[/email]
        Servername site2
	DocumentRoot /var/www/site2
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/site2/>
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


Site 3:

<VirtualHost site3>
	ServerAdmin [email]tec@testserver.123.com[/email]
        Servername site3 
	DocumentRoot /var/www/site3
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/site3/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>t

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

This site will only be accessed internally so i am trying to use a simple name like site2 instead of site2.somedomain.com. I also have these added to the internal DNS server and able to ping the name to the correct IP. Any help that can be supplied would be more then appreciated. Thanks in advance!

---

### Post by e24ohm on 2010-06-15
> **eric_1982 said:**
> I am really struggling getting Virtual Host to work correctly on Ubuntu 10.04. I had no issues with 9.10 but am just having no luck after upgrading. I keep getting the following message when restarting apache. 

[Tue Jun 15 09:50:56 2010] [warn] VirtualHost site2:0 overlaps with VirtualHost site3:0, the first has precedence, perhaps you need a NameVirtualHost directive
[Tue Jun 15 09:50:56 2010] [warn] NameVirtualHost *:80 has no VirtualHosts

It keeps on defaulting all web request to the root folder /var/www/.

I am looking on getting 3 sites working. One that defaults to the root dir /var/www, and site2 and site3 in there own folders inside /var/www/. Example: /var/www/site2 and /var/www/site3.

I have create a file called site2 and site3 in /etc/apache2/sites-available and have done a sudo a2ensite site2 and sudo a2ensite site3. After doing this I have done and /etc/init.d/apache2 reload. 

Listed below is what my two site config files look like. I also have the default config file with no modifications to it as well. 

site2:

<VirtualHost site2>
	ServerAdmin [email]tec@testserver.123.com[/email]
        Servername site2
	DocumentRoot /var/www/site2
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/site2/>
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


Site 3:

<VirtualHost site3>
	ServerAdmin [email]tec@testserver.123.com[/email]
        Servername site3 
	DocumentRoot /var/www/site3
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/site3/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>t

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

This site will only be accessed internally so i am trying to use a simple name like site2 instead of site2.somedomain.com. I also have these added to the internal DNS server and able to ping the name to the correct IP. Any help that can be supplied would be more then appreciated. Thanks in advance!

I just have the following in my site file located "/etc/apache2/site-available"

<VirtualHost *>
ServerName music
ServerAlias music
DocumentRoot /var/www/music
</VirtualHost>

---

### Post by stmiller on 2010-06-15
Yeah you are missing the 'star' * 

You need:

```
<Virtualhost *:80>
```

at the top. Not site2, or site3. Don't put that there. :)

---

### Post by beowulf1416 on 2010-06-15
what you could also do is to set up virtual hosting by port addresses like this:

for site2
```

<Virtualhost *:81>
...

```

for site3
```

<Virtualhost *:82>
...

```

and add the Listen directive for every port you want configured. eg:
```

Listen 81
Listen 82

```

its how my dev machine is set up.

---

### Post by eric_1982 on 2010-06-15
I have tried adding ServerAlias and changed virtual host to <VirtualHost *:80> and then running /etc/init.d/apache2 reload.

Still no luck. What am I missing? They keep defaulting to the root path. I have just an html file in site2 dir and a drupal install in site3. I can navigate to it if I put site2/site2 or site3/site3. I have to have something wrong or missing a setting some were. I have check to make sure I don't have a capital letter or anything weird like that. Have anything else I can try? I really appreciate the help so far!

Here is what site 2 config currently looks like in /etc/apache2/sites-enabled:

<VirtualHost *:80>
	ServerAdmin [email]tec@testserver.123.com[/email]
        Servername site2
        ServerAlias site2
	DocumentRoot /var/www/site2
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/site2/>
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

---

### Post by e24ohm on 2010-06-15
> **eric_1982 said:**
> I have tried adding ServerAlias and changed virtual host to <VirtualHost *:80> and then running /etc/init.d/apache2 reload.

Still no luck. What am I missing? They keep defaulting to the root path. I have just an html file in site2 dir and a drupal install in site3. I can navigate to it if I put site2/site2 or site3/site3. I have to have something wrong or missing a setting some were. I have check to make sure I don't have a capital letter or anything weird like that. Have anything else I can try? I really appreciate the help so far!

Here is what site 2 config currently looks like in /etc/apache2/sites-enabled:

<VirtualHost *:80>
	ServerAdmin [email]tec@testserver.123.com[/email]
        Servername site2
        ServerAlias site2
	DocumentRoot /var/www/site2
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/site2/>
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
You mention Drupal. I had this problem when I installed Drupal first. I am not sure if I installed Drupal correctly or not, and I am not sure if that was the only issue, but I was force to blow Drupal away, and start from scratch. You could also make virtual IP addresses, and associate the website with that IP address, and make the needed updates in your DNS records; however, that is not a nice solution. I ended up having to do this for a client, becuase they were having the same issue as I was, and as you are reporting.

---

### Post by eric_1982 on 2010-06-15
Still no luck. I blew away the drupal site and created a real basic index.html file and then reload apache. I am still being brought to the default dir /var/www/

Any other things to try?

One other note. I have tried clearing history and cache in my browser.

---

### Post by koenn on 2010-06-15
reduce the host definitions to the bare minimum, like the one e24ohm mentioned a few posts back.

See if that allows you to distinguish by name between the 2 or 3 sites.
once you have that working, add extra styff such as ScriptAlias as needed.

I doubt you really want to define 'directory /" and the docs alias more than once.

---

### Post by eric_1982 on 2010-06-15
Ok I changed site2 and site3 config and left the default file alone. I then reloaded apache2 and cleared browser cache and histroy. Still no go. :(

This is what my config files look like 

<VirtualHost *>
ServerName site2
ServerAlias site2
DocumentRoot /var/www/site2
</VirtualHost>




<VirtualHost *>
ServerName site3
ServerAlias site3
DocumentRoot /var/www/site3
</VirtualHost>


This is what the default file looks like:



<VirtualHost *>
	ServerAdmin webmaster@localhost
        Servername 192.168.1.253
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

---

### Post by koenn on 2010-06-15
"no go" doesn't say much.

what urls are you using to test this, 
what do you get in your browser,
and what do the apache access and error logs say ?

---

### Post by e24ohm on 2010-06-15
> **eric_1982 said:**
> Ok I changed site2 and site3 config and left the default file alone. I then reloaded apache2 and cleared browser cache and histroy. Still no go. :(

This is what my config files look like 

<VirtualHost *>
ServerName site2
ServerAlias site2
DocumentRoot /var/www/site2
</VirtualHost>




<VirtualHost *>
ServerName site3
ServerAlias site3
DocumentRoot /var/www/site3
</VirtualHost>


This is what the default file looks like:



<VirtualHost *>
	ServerAdmin webmaster@localhost
        Servername 192.168.1.253
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

Yeah this was a pain, and I will look when I get back into the office at my notes for you. right off the top of my head, the only way I was able to get around this issue once I had a Drupal installed first. Was to make the sites IP based, and use virtual ip address ports on the NIC. I then associated the IP address with the domain name/site name and specified the virtual ip address I used.

Again, once i am in the office I will look at my notes for you.

---

### Post by eric_1982 on 2010-06-15
The URL(s) I am using [http://site2](http://site2) or [http://site3](http://site3). It keeps defaulting to the root dir /var/www/. I am not seeing much in the logs. Here is what I am seeing thought encase i overlooked something:


**/var/log/apache2/error.log:**

[Tue Jun 15 16:11:41 2010] [notice] Graceful restart requested, doing restart
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/idn.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imagick.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imap.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Tue Jun 15 16:11:42 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations


**/var/log/apache2/access.log**


192.168.1.139 - - [15/Jun/2010:15:45:59 -0500] "GET / HTTP/1.1" 200 484 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.9) Gecko/20100401 Ubuntu/9.10 (karmic) Firefox/3.5.9"
192.168.1.139 - - [15/Jun/2010:15:46:02 -0500] "GET / HTTP/1.1" 200 483 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.9) Gecko/20100401 Ubuntu/9.10 (karmic) Firefox/3.5.9"
192.168.1.139 - - [15/Jun/2010:15:46:08 -0500] "GET / HTTP/1.1" 200 484 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.9) Gecko/20100401 Ubuntu/9.10 (karmic) Firefox/3.5.9"
192.168.1.139 - - [15/Jun/2010:15:46:08 -0500] "GET /favicon.ico HTTP/1.1" 404 498 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.9) Gecko/20100401 Ubuntu/9.10 (karmic) Firefox/3.5.9"
192.168.1.139 - - [15/Jun/2010:15:46:09 -0500] "GET / HTTP/1.1" 200 483 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.9) Gecko/20100401 Ubuntu/9.10 (karmic) Firefox/3.5.9"
192.168.1.139 - - [15/Jun/2010:15:46:11 -0500] "GET /favicon.ico HTTP/1.1" 404 498 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.9) Gecko/20100401 Ubuntu/9.10 (karmic) Firefox/3.5.9"
192.168.1.139 - - [15/Jun/2010:15:46:11 -0500] "GET /favicon.ico HTTP/1.1" 404 498 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.9) Gecko/20100401 Ubuntu/9.10 (karmic) Firefox/3.5.9"
192.168.1.139 - - [15/Jun/2010:15:47:46 -0500] "GET / HTTP/1.1" 200 484 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.9) Gecko/20100401 Ubuntu/9.10 (karmic) Firefox/3.5.9"
192.168.1.139 - - [15/Jun/2010:15:47:51 -0500] "GET /site3 HTTP/1.1" 301 539 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.9) Gecko/20100401 Ubuntu/9.10 (karmic) Firefox/3.5.9"
192.168.1.139 - - [15/Jun/2010:15:47:51 -0500] "GET /site3/ HTTP/1.1" 200 388 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.9) Gecko/20100401 Ubuntu/9.10 (karmic) Firefox/3.5.9"
192.168.1.3 - - [15/Jun/2010:15:48:09 -0500] "GET / HTTP/1.1" 200 484 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.2; en-US; rv:1.9.1.5) Gecko/20091102 Firefox/3.5.5 ( .NET CLR 3.5.30729)"
127.0.0.1 - - [15/Jun/2010:15:48:43 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [15/Jun/2010:15:48:43 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [15/Jun/2010:15:48:43 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [15/Jun/2010:15:48:43 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [15/Jun/2010:15:48:43 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [15/Jun/2010:15:48:43 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [15/Jun/2010:15:48:43 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
192.168.1.139 - - [15/Jun/2010:15:48:52 -0500] "GET / HTTP/1.1" 200 484 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.9) Gecko/20100401 Ubuntu/9.10 (karmic) Firefox/3.5.9"
127.0.0.1 - - [15/Jun/2010:16:11:41 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [15/Jun/2010:16:11:41 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [15/Jun/2010:16:11:41 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [15/Jun/2010:16:11:41 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [15/Jun/2010:16:11:41 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"




**/var/log/apache2/other_vhosts_access.log**


testserver.tec.local:80 192.168.1.3 - - [15/Jun/2010:09:34:13 -0500] "GET / HTTP/1.1" 404 492 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.2; en-US; rv:1.9.1.5) Gecko/20091102 Firefox/3.5.5 ( .NET CLR 3.5.30729)"
testserver.tec.local:80 192.168.1.3 - - [15/Jun/2010:09:34:13 -0500] "GET /favicon.ico HTTP/1.1" 404 498 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.2; en-US; rv:1.9.1.5) Gecko/20091102 Firefox/3.5.5 ( .NET CLR 3.5.30729)"
testserver.tec.local:80 192.168.1.3 - - [15/Jun/2010:09:34:17 -0500] "GET /favicon.ico HTTP/1.1" 404 498 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.2; en-US; rv:1.9.1.5) Gecko/20091102 Firefox/3.5.5 ( .NET CLR 3.5.30729)"

---

### Post by koenn on 2010-06-15
your logs are showing
- no lookup for site2
- a successful lookup for site3 : 
192.168.1.139 - - [15/Jun/2010:15:47:51 -0500] "GET /site3/ HTTP/1.1" **200** 388 "-" 

that kind of contradicts what you say. I don't have an explanation for that.

you might want to try that again,
or set up logging for each vhost separately,  with a higher log level

[http://httpd.apache.org/docs/2.2/mod/core.html#loglevel](http://httpd.apache.org/docs/2.2/mod/core.html#loglevel)

---

### Post by matrimubu on 2010-07-26
change the NameVirtualHost *:80 in ports.conf to NameVirtualHost *

make sure this is the same as what is in apache2.conf and in the <VirtualHost *> 
element of each of your sites.

---

