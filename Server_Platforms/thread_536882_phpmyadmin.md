---
title: "phpmyadmin"
date: 2007-08-28
forum: Server Platforms
---

### Post by kenmiles on 2007-08-28
I have installed phpmyadmin but get the following error when trying to connect -

The server encountered an internal error or misconfiguration and was unable to complete your request.
Please contact the server administrator, <email address> and inform them of the time the error occurred, and anything you might have done that may have caused the error.
More information about this error may be available in the server error log.

This is the entry from the error log.

[Tue Aug 28 14:31:13 2007] [error] [client ::1] Premature end of script headers: index.php
[Tue Aug 28 14:31:13 2007] [error] [client ::1] SoftException in Application.cpp:193: Script "/var/www/public_html/phpmyadmin/index.php" resolving to "/usr/share/phpmyadmin/index.php" not within configured docroot
[Tue Aug 28 14:31:13 2007] [error] [client ::1] *** glibc detected *** /usr/lib/suphp/suphp: double free or corruption (fasttop): 0x08070ab0 *

I am using Ubuntu 6.10 and apache2, php5.

Can anyone help with this please?

Regards, Kenneth.
[http://kmiles.co.uk](http://kmiles.co.uk)

---

### Post by LaRoza on 2007-08-28
> **kenmiles said:**
> 
This is the entry from the error log.

[Tue Aug 28 14:31:13 2007] [error] [client ::1] Premature end of script headers: index.php
[Tue Aug 28 14:31:13 2007] [error] [client ::1] SoftException in Application.cpp:193: Script "/var/www/public_html/phpmyadmin/index.php" resolving to "/usr/share/phpmyadmin/index.php" not within configured docroot
[Tue Aug 28 14:31:13 2007] [error] [client ::1] *** glibc detected *** /usr/lib/suphp/suphp: double free or corruption (fasttop): 0x08070ab0 *

I am using Ubuntu 6.10 and apache2, php5.

How did you try to connect?

(Using [nowiki]]http://ipAddress/phpmyadmin[/nowiki] only works if you have an alias)

---

### Post by iskatyel on 2007-08-28
Tell us about your Apache2 setup.  What sites do you have enabled and how are they setup? 
edit: For sites enabled:
cd /etc/apache2/sites-enabled
ls
and then use more or nano or vim to look at each of the sites and let us know.

---

### Post by kenmiles on 2007-08-28
> **iskatyel said:**
> Tell us about your Apache2 setup.  What sites do you have enabled and how are they setup? 
edit: For sites enabled:
cd /etc/apache2/sites-enabled
ls
and then use more or nano or vim to look at each of the sites and let us know.

Tis is my sites enabled file entry - 
DocumentRoot /var/www/public_html
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/public_html/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
		#RedirectMatch ^/$ /apache2-default/
	</Directory>

To the previous reply I call it by [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Hope this helps and thanks for the replys.
Regards, Kenneth.

---

### Post by iskatyel on 2007-08-28
Your apache config looks fine.  I did some searching on the errors you included and it looked like essentially everyone seeing the same errors was running ubuntu and this error:
```
*** glibc detected *** /usr/lib/suphp/suphp: double free or corruption (fasttop): 0x08070ab0 
```
could be an error from a package having been compiled improperly or a bug in php or mysql.  Mysql did fix some bugs last fall that caused this under certain conditions.  But, since index.php is cited as the one starting the problem, it may have fed improper data causing the rest of the errors.  Does anyone know if there is a bug with the phpmyadmin package in 6.10?  I don't see one reported on launchpad.

Can you run apt-get update and then apt-get upgrade and see if that fixes the package?

---

### Post by kenmiles on 2007-08-28
> **iskatyel said:**
> 
Can you run apt-get update and then apt-get upgrade and see if that fixes the package?

I have done as you suggest and this is the result.

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So it looks like I might have to do without phpmyadmin.
Thanks again for your help, Kenneth.

---

