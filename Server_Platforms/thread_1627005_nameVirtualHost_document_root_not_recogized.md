---
title: "nameVirtualHost document root not recogized"
date: 2010-11-20
forum: Server Platforms
---

### Post by bobnw on 2010-11-20
(regular Ubuntu 10.04 with Apache server installed)

Can bring up php files and sites under localhost which is the the default site.  I have a second virtual host set up under sites-enalbed.  It was set up by pasting in the default site text and changing the site ServeName and directory names. 

When I enter 
          [http://test.wdv/index.php](http://test.wdv/index.php)
into a broswer I get 
      404 Not Found 
      Apache/2.2.14 (Ubuntu) Server at test.wdv Port 80

The corresponding line in the  Apache error log contains 
      script '/var/www/mqiTest.php' not found

It looks like Apache has picked up the site name but not the document root. It looked under the default document root even though it identified itself as the test.wdv server in the error message.   

The contents of sites-enabled/test.wdv are:
<VirtualHost *:80>
	ServerAdmin  [email]bobn@servin.us[/email] 
	DocumentRoot /wdv/test/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	
	<Directory /wdv/test/>
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

	ErrorLog /var/log/apache2/test.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	#CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
#end test.wdv avail
</VirtualHost>

How do I fix this?

Thanks for your suggestions

---

### Post by wongo888 on 2010-11-21
To add a new virtual host, first copy the default provided:

```
$ sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/example.com
```

Assuming your web files are in /var/www/vhosts/example.com, add the "ServerName" and adjust the "DocumentRoot".

```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName www.example.com
	ServerAlias example.com
	DocumentRoot /var/www/vhosts/example.com

...rest of file...


```

Ensure your files are in the right place and are readable by apache. Then enable the site using the tool provided and reload the server configuration.

```
$ sudo a2ensite example.com
Enabling site example.com.
Run '/etc/init.d/apache2 reload' to activate new configuration!
$ sudo /etc/init.d/apache2 reload
 * Reloading web server config apache2
   ...done.

```

More at:

[https://help.ubuntu.com/10.04/serverguide/C/httpd.html#http-basic-settings](https://help.ubuntu.com/10.04/serverguide/C/httpd.html#http-basic-settings)

---

### Post by Ryan Dwyer on 2010-11-21
You didn't specify the ServerName in the virtualhost block.

---

### Post by bobnw on 2010-11-21
that's it

thanks so much... it would have taken me a long time to find the the missing line

---

