---
title: "PHP installed and tested to work but not always :|"
date: 2009-12-17
forum: Server Platforms
---

### Post by amn108 on 2009-12-17
Unfortunately, I cannot describe the issue better in the limited space of the subject line.

I have set up both Apache and PHP 4 and 5 numerous time in the past, always on Windows though. It worked like a charm.

Currently, I am on Ubuntu 9.10 and have instealled apache2 and php5 package which also installed libapache2-mod-php5 and basically everything that is needed to run both. They do run, and I have also tested a phpinfo() method output, when putting it in a index.php script and accessing "/" on a virtual server. It works and I get the typical PHP information page.

The problem is it DOES NOT work - i.e. I do not get any PHP processing and only am offered to actually download a PHP file (as text/plain, I presume?) when trying to access any other .php suffixed URL (i.e. a PHP file) explicitly. For example having a 'phpinfo()' call in a file 'phpinfo.php' and trying to request it using 'http://localhost/phpinfo.php' gives me the download dialog.

My PHP mime types are set up and the php5 module is loaded.

I am using a virtual host setup, which is loaded with:

<VirtualHost youbanner:80>
	ServerAdmin [email]admin@example.com[/email]

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
</VirtualHost>

May it have anything to do with file permissions? I tried to use the default virtual host and then it works. But then again, the phpinfo.php file has the same permissions as index.php which works.

I attach my /etc/apache2.conf file.

This is weird...

---

