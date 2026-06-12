---
title: "unable to load phpMyAdmin in 8.04"
date: 2009-07-07
forum: Server Platforms
---

### Post by DDBrewer on 2009-07-07
I'm a newbie who's been using Ubuntu 8.04 for about 7 months (as the only OS on my machine, no partition).  I'm trying to get LAMP working on my localhost, but can't get phpMyAdmin to load.  

I installed Apache, MySQL, PHP, and phpMyAdmin following the directions at [http://maketecheasier.com/setting-up-a-lamp-server-in-ubuntu-hardy-heron/2008/08/06]("http://maketecheasier.com/setting-up-a-lamp-server-in-ubuntu-hardy-heron/2008/08/06").  Everything worked like the instructions showed except that I was not prompted for a new password for the MySQL root user.  

When I try to go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin), I get a pop-up dialog box that says "Download this file? File Type: “application/x-httpd-php type”.  You have no application able to open “”. You can download it instead."  If I cancel, the page doesn't change from what it was before.  If I download, the file seems to be a PHP script (NAFHaMEx.part), but with nothing that references phpMyAdmin except for the HTML title tag. What is going wrong?  

I know that Apache works (I get "It works" when I point my browser to [http://localhost](http://localhost)).  I know that PHP works, because a test PHP file with the single line "<?php phpinfo(); ?>" gives the PHP info. To address a possible password problem with MySQL, I tried to change the password with sudo dpkg-reconfigure mysql-server-5.0 at the terminal.  This made no difference.  

I've reinstalled Apache, PHP, MySQL, and phpMyAdmin via Synaptic, and that didn't help, either (still not prompted for root user password in MySQL).  

Any advice or tips would be greatly appreciated!  

Thank you!

---

### Post by DDBrewer on 2009-07-07
I spent a few more hours digging, and found one thread on another forum ([http://www.howtoforge.com/forums/archive/index.php/t-28610.html]("http://www.howtoforge.com/forums/archive/index.php/t-28610.html")) that gave me a near-solution.  It turns out that [http://localhost/phpmyadmin](http://localhost/phpmyadmin) gives the problematic result I described initially, but that [http://127.0.0.1/phpmyadmin](http://127.0.0.1/phpmyadmin) lets me into phpMyAdmin and works as expected.  So I guess my question now is how do I get localhost to be treated the same as 127.0.0.1 with respect to phpmyadmin?

Thank you for any help you might be able to give.

---

### Post by wojox on 2009-07-07
Go to /etc/apache2/sites-enabled

Look for a default file and post it here please.

---

### Post by DDBrewer on 2009-07-07
wojox,

The file in that directory is called 000-default.  Here is its contents:

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


Thank you!

---

### Post by wojox on 2009-07-07
Where it says

Allow from 127.0.0.0/255.0.0.0 ::1/128   skip down and add 
Allow from localhost

I would also turn off your server signature so people don't know what your running. It helps keep the bad people out.

---

### Post by DDBrewer on 2009-07-07
Thank you very much for the tip on ServerSignature (I didn't set it that way -- it must be the default).  

I added a line that says "Allow from localhost" and saved.  However, I still get the same behavior from [http://localhost/phpmyadmin](http://localhost/phpmyadmin).  That is, it still doesn't load phpmyadmin.  

Any other ideas?

Thanks again.

---

### Post by wojox on 2009-07-07
Try this

```
sudo gedit /etc/apache2/apache2.conf
```

Include the following line at the bottom of the file, save and quit. 

```
Include /etc/phpmyadmin/apache.conf
```

Let me know if that works

---

### Post by DDBrewer on 2009-07-07
I had already inserted that line into that file when pursuing a solution earlier (before my initial post).  So that doesn't seem to affect the 127.0.0.1 vs. localhost behavior.

Any other ideas?  If I have to live with this, I can.  

Thank you!

---

### Post by wojox on 2009-07-07
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Check out that site.

---

### Post by DDBrewer on 2009-07-07
Thank you.  I had already looked at that site for other problems I was having.  I just tried typing "echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn" at the terminal to see if that would help.  No such luck.  I'll just live with 127.0.0.1 for accessing phpmyadmin, unless any other ideas come to mind. 

Thank you _very much_ for your help!

---

### Post by Kolipoki on 2009-07-08
Hihi, still a newb here, but you might want to check /etc/mysql/my.cnf and try to comment out the line for bind-address, so that it says:

#bind-address           = 127.0.0.1

This will make MySQL listen to all interfaces (thanks howtoforge.com). Again, not sure if this is the problem, but somehow I feel your problem might not be from Apache. Cheers...

---

### Post by DDBrewer on 2009-07-10
Kolipoki,

Excellent suggestion!  That fixes the problem.

Thank you!

---

### Post by Kolipoki on 2009-07-10
Great, glad that it worked. May I suggest you brand this thread as "Solved", so it helps searchers pick first those results that are solved. ;)

---

