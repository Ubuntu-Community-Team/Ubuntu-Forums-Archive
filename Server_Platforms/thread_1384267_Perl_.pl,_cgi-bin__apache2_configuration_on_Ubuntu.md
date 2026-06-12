---
title: "Perl .pl, cgi-bin  apache2 configuration on Ubuntu 9.10"
date: 2010-01-18
forum: Server Platforms
---

### Post by savyn on 2010-01-18
Hello Everyone,

Very new to Ubuntu (linux) in general and read various forum and threads to get .pl file to run on a new Ubuntu 9.10. 

My cgi-bin is in /var/www/site/cgi-bin. The server will run 2 websites site1 and site 2. Site2 is html only and site1 has some cgi and pl files. Everytime i get to the cgi-bin/other_director the browser tries download the file or even if going directly to index.pl. Please find attached my site-available for both default and site1 for your consideration. 
I also ran a2ensite site1 and a2ensite site2, the reloaded the apache2 server

Any help is very much appreciated.


many thanks
Savyn
Default
> 
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

	ScriptAlias /cgi-bin/ /var/www/site1/cgi-bin/
	<Directory "/var/www/site1/cgi-bin">
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



site1
> <VirtualHost *:80>
	ServerAdmin web@localhost
	ServerName [www.site1.com](www.site1.com)
	ServerAlias site1.com

	DocumentRoot /var/www/site1/
	DirectoryIndex index.html index.pl login.pl index.htm

	ScriptAlias /cgi-bin/ /var/www/site/cgi-bin/
	<Directory "/var/www/site1/cgi-bin/">
		Options ExecCGI
		AddHandler cgi-script .cgi .pl
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
</VirtualHost>


---

### Post by savyn on 2010-01-18
Any ideas, or how would you do this on your server?
Thanks

---

### Post by manikram1982 on 2010-08-11
Dear All,

I am trying to configure cgi-bin in my user account. I have modified /etc/apache2/sites-available/default as show below.

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /home/raghavendra/public_html/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/raghavendra/public_html/>
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

I am able to see the content under /home/raghavendra/public_html/index.html when I run [http://localhost](http://localhost)
But, I am not able to list the directories and execute cgi scripts which are under ~/public_html/cgi-bin

Please let me know how to fix this issue. TIA.

--Raghavendra.

---

