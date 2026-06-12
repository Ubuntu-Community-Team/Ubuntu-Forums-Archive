---
title: "Apache2 with VitualHosts"
date: 2009-11-27
forum: Server Platforms
---

### Post by drewsmith on 2009-11-27
I am trying to get VirtualHosts working.  I have dissable the default site and created a new site.  The configuration file is called mysites and contains the following

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName [www.yourlocalpcrepairman.co.uk](www.yourlocalpcrepairman.co.uk) 
	DocumentRoot /var/www/html
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


<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName dsmith.homeip.net
        DocumentRoot /var/www/html/drew
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



<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName dsmith.homelinux.net
        DocumentRoot /var/www/html
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
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName [www.yourlocalpcrepairman.co.uk](www.yourlocalpcrepairman.co.uk) 
	DocumentRoot /var/www/html
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


<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName dsmith.homeip.net
        DocumentRoot /var/www/html/drew
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



<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName dsmith.homelinux.net
        DocumentRoot /var/www/html
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

I thought it worked by when I restarted the machine all three domains point to the one site i.e. [www.yourlocapcrepairman.co.uk](www.yourlocapcrepairman.co.uk)  can anyone point out what might be wrong.

I did enable the site with a2ensite mysites and reloaded apache.

Any help would be great.

---

### Post by Lars Noodén on 2009-11-27
It's hard to tell where one file leaves off and another begins.  

Did you set /etc/apache2/apache2.conf to allow name-based virtual hosts?

[indent]
NameVirtualHost *
[/indent]

[http://wiki.apache.org/httpd/CommonMisconfigurations](http://wiki.apache.org/httpd/CommonMisconfigurations)
[http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)

---

### Post by drewsmith on 2009-11-27
> **Lars Noodén said:**
> It's hard to tell where one file leaves off and another begins.  

Did you set /etc/apache2/apache2.conf to allow name-based virtual hosts?
[INDENT]
NameVirtualHosts *
[/INDENT][http://wiki.apache.org/httpd/CommonMisconfigurations](http://wiki.apache.org/httpd/CommonMisconfigurations)
[http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)


I have tried this in before but did not make any difference.

I have added it again but got  the following error

Invalid command 'NameVirtualHosts', perhaps misspelled or defined by a module not included in the server configuration


Any thoughts?

---

### Post by Lars Noodén on 2009-11-27
> **drewsmith said:**
> ...got  the following error

Invalid command 'NameVirtualHosts', perhaps misspelled or defined by a module not included in the server configuration


Without it you can't use name virtual hosts.  
Somehow a typo got in there.  Try "NameVirtualHost" with no "s"
Try that.

Then check that the VirtualHost directives match the NameVirtualHost directive exactly.  i.e. "*:80"

---

### Post by drewsmith on 2009-11-27
> **Lars Noodén said:**
> Without it you can't use name virtual hosts.  
Somehow a typo got in there.  Try "NameVirtualHost" with no "s"
Try that.

Then check that the VirtualHost directives match the NameVirtualHost directive exactly.  i.e. "*:80"

Sorted:

I think the problem related to ports.conf file.  The vitrual host was already stated there.

Thanks for the help.

---

### Post by Vegan on 2009-11-27
There is no reason to modify ports.conf or apache2.conf, instead the httpd.conf is where user settings are to be stored.

I have a piece on the site on setting up Apache2, its in the LAMP area of the Linux section.

---

