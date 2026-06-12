---
title: "Ghost host &amp;&amp; virtualhost not working properly"
date: 2010-08-11
forum: Server Platforms
---

### Post by Stoneface on 2010-08-11
I just setup a LAMP on my Ubuntu 10.0.4 desktop using tasksel with PMA and am working on configuring virtual hosts to more easily browse sites I will be development and or testing on this localhost.I have two problems. Every time I restart Apache or do some work on a virtualhost I get this error:```
$ sudo /etc/init.d/apache2 restart
sudo: unable to resolve host ubuntu
 * Restarting web server apache2                                                apache2: apr_sockaddr_info_get() failed for ubuntu
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
 ... waiting apache2: apr_sockaddr_info_get() failed for ubuntu
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

```

I only have a virtualhost default and wordpress. How is this error caused and how can I resolve it?
Second issue, when I go to wordpress-dev my /etc/hosts file neatly directs me to my virtualhost Wordpress residing in /var/www/wordpress, but when I click to see a comment I get a url with localhost in it: ```
http://localhost/wordpress/?p=1#comments
```. Is this a Wordpress permalinks issue or is this a virtualhost missconfiguration? 

Here is my virtualhost wordpress ```
<VirtualHost 127.0.1.1:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www/wordpress/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/wordpress/>
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

And here my hosts file: ```
127.0.0.1	localhost
127.0.1.1	wordpress-dev

# The followinag lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by Stoneface on 2010-08-11
Well, thanks to [Unixmen]("http://www.unixmen.com/linux-tutorials/documentations-a-howto/941-apache2-aprsockaddrinfoget-failed-for") I solved some errors by adding```
ServerName localhost
``` to ```
/etc/apache2/apache2.conf
```. Now I get this after restarting Apache ```
$sudo /etc/init.d/apache2 restart
sudo: unable to resolve host ubuntu
 * Restarting web server apache2                                                 ... waiting                               
```

Why I get this: ```
sudo: unable to resolve host ubuntu 
``` after restarting and why wordpress-dev still shows localhost in urls I do not know yet.

---

### Post by Stoneface on 2010-08-11
After reading thread [http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361) I added ```
127.0.1.1 ubuntu
``` to /etc/hosts and restarted Apache ```
sudo /etc/init.d/apache2 restart
``` . Now all is good ```
* Restarting web server apache2                                                 ... waiting                                               [ OK ]
```
I now remember removing it as it did not seem needed there. I guess it is.
Now I will see if I can resolve the odd url issue with localhost appearing in the url of my virtualhost wordpress with hostname wordpress-dev like this: ```
http://localhost/wordpress/?p=1#comments
```

---

### Post by Stoneface on 2010-08-11
Well I adjusted some data in wp-options to make site url and home links [http://wordpress-dev](http://wordpress-dev) and activated permalinks. Home is correct now and links to [http://wordpress-dev](http://wordpress-dev), but all pages and posts give 404s: ```
[Wed Aug 11 01:03:08 2010] [error] [client 127.0.1.1] File does not exist: /var/www/wordpress/about, referer: http://wordpress-dev/
[Wed Aug 11 01:03:49 2010] [error] [client 127.0.1.1] File does not exist: /var/www/wordpress/about, referer: http://wordpress-dev/
[Wed Aug 11 01:06:28 2010] [error] [client 127.0.1.1] File does not exist: /var/www/wordpress/about, referer: http://wordpress-dev/

```

If I turn off permalinks all urls are OK -ie [http://wordpress-dev/?page_id=6](http://wordpress-dev/?page_id=6) works - and lead to all pages and all with [http://wordpressd-dev](http://wordpressd-dev) as base url. But why do permalinks not work?

---

### Post by Stoneface on 2010-08-11
Well there appeared to be an error in my .htaccess, which needed fixing. All is peachy with this .htaccess now: ```
# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>

# END WordPress
```

:popcorn:

---

