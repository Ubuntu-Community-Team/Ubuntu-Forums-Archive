---
title: "Configuring Apache for Subdomain"
date: 2011-01-17
forum: Server Platforms
---

### Post by mclimber43 on 2011-01-17
I recently set up a website with Apache (call it mysite.com).  I want to add a subdomain (login.mysite.com) with SSL encryption.  I have the subdomain pointing to my IP address and I have set up the encryption.  However, I can access my login page by going to [https://login.mysite.com](https://login.mysite.com) AND [https://mysite.com](https://mysite.com).  I want to only have the page load with [https://login.mysite.com](https://login.mysite.com).  I have pasted apache config file details below.  

Thanks for any help.  I have scoured google and haven't been able to find a solution.

```
<VirtualHost *:80>
	ServerName www.mysite.com
	ServerAlias mysite.com
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

<VirtualHost *:443>
	
        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/apache.pem
	ServerName login.mysite.com
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/ssl
        <Directory />
                Options FollowSymLinks -Indexes
                AllowOverride None
        </Directory>
        <Directory /var/www/ssl>
                Options Indexes FollowSymLinks MultiViews -Indexes
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

```

---

### Post by Thirtysixway on 2011-01-17
Is this all in, say, httpd.conf? I got it working but my setup is a little different.  I have each site in /etc/apache2/sites-available. say have one site in a file called mysite.com and the other in a file called mysite.com-secure.

/etc/apache2/sites-available/mysite.com
```

<VirtualHost *:80>
	ServerName www.mysite.com
	ServerAlias mysite.com
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

/etc/apache2/sites-available/mysite.com-secure
```

NameVirtualHost *:443

<VirtualHost *:443>
	
        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/apache.pem
	ServerName login.mysite.com
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/ssl
        <Directory />
                Options FollowSymLinks -Indexes
                AllowOverride None
        </Directory>
        <Directory /var/www/ssl>
                Options Indexes FollowSymLinks MultiViews -Indexes
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

```

and then enable the sites using the following commands
```

sudo a2ensite mysite.com
sudo a2ensite mysite.com-secure

```
Note that in the above config file I added 
```

NameVirtualHost *:443

```
That's what I had to add to mine to get it to work properly. But either way, I'd split my config files into the sites-available folder for good practice.

---

### Post by mclimber43 on 2011-01-17
Thanks for the response.  Yes, the code that I had before was from sites-available.  I split the file in two and separately enabled each.  Unfortunately, no change.

---

### Post by James78 on 2011-01-17
The SSL VirtualHost you have is the very first SSL VirtualHost that is seen by Apache, so it is the default VirtualHost for all unmatched domains in SSL (e.g. mysite.com is unmatched in any SSL VirtualHosts, so the very first SSL VirtualHost seen is returned, in this case login.mysite.com).

The fix is to create a set of default VirtualHosts. If you've ever seen the "default" and "default-ssl" configs, that's what those are for. They capture all the extra. You need to configure a default VirtualHost to capture all unmatched instances.

For example, here's mine. What it does is: it captures all unmatched (no other VHost matches domain name) SSL VirtualHosts since it's the first SSL VirtualHost seen by Apache; then it returns a 400 bad request. So essentially, what you see happening: I go to [https://mysite.com](https://mysite.com), and it returns 400 bad request.
```
# Default SSL VHost
<VirtualHost 192.168.1.120:443>
CustomLog /var/log/virtualmin/access_log combined
ErrorLog /var/log/virtualmin/error_log

RewriteEngine On
# Return 400 bad request
RewriteRule . - [R=400]

SSLEngine on
SSLCertificateFile /home/user/ssl.cert
SSLCertificateKeyFile /home/user/ssl.key
SSLCACertificateFile /home/user/ssl.ca-bundle
</VirtualHost>
```
As for my port 80 default VHost, it simply returns a web page that says "this address is incorrect, please use correct domain". You could return a webpage for the SSL VHost instead if you really wanted to like I did in the 80 VHost (or make port 80 default VHost return 400 bad request), but I think 400 bad request fits better for a unmatched SSL VHost (I'd rather it return 400 bad request on [https://mysite.com](https://mysite.com) instead of serving a page saying "incorrect page"), and the webpage for the unmatched 80 VHost.

---

