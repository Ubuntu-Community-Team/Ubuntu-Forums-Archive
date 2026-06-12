---
title: "Apache2 + Virtual Host: PHP Issue"
date: 2010-08-04
forum: Server Platforms
---

### Post by ofir_k on 2010-08-04
Hello,

I just downgraded php to php5.2 by using the script from [here]("http://ubuntuforums.org/showpost.php?p=9201854&postcount=6").

I have a virtual host site configured:
```

#
#  sites-testing (/etc/apache2/sites-available/sites-testing)
#
<VirtualHost *:80>
        ServerAdmin webmaster@sites-testing
        ServerName  sites-testing

        # Indexes + Directory Root.
        DocumentRoot /var/www/sites/

	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>

	<Directory /var/www/sites/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>
	
</VirtualHost>

```

I added the appropriate line in /etc/hosts and everything works just fine (I have there a drupal site on one directory, a Wordpress site on another one, and PHPBB forum on the last one).

Everything works except when I enter / I get a download dialog to download the index.php file.

I mean, when I enter [http://sites-testing/index.php](http://sites-testing/index.php) it works, 
but when I enter [http://sites-testing/](http://sites-testing/) I get the source of index.php

There is no error in error.log and no access entry in other_vhosts_access.log for when I try to access [http://sites-testing/](http://sites-testing/)

Any idea how to fix it?

Help is really appreciated!
Ofir

---

### Post by ruffEdgz on 2010-08-04
Do you have .htaccess files for all those services your host?

I'm asking because you set the follow for your /var/www/sites part of your config:
```

AllowOverride All

```
This will allow those to override any configuration that is found accessing the directory /var/www/sites/.

I just have the default setup of apache2 on my test server and I don't have that issue with downloading the index.php file when not specified. Your configuration is really no different except for the Directory location and the change to 'AllowOverride' to 'All' (I have it set to 'None').

Hope this helps.

---

### Post by ofir_k on 2010-08-04
Thanks for your reply.

I changed that line to:
```
AllowOverride None
```

and I still have this issue.

I am using mod_rewrite, so I thought it was the cause, but disabling it didn't solve the problem.

Everytime I start and stop apache, I get this error messages:
```
[Thu Aug 05 00:12:33 2010] [notice] caught SIGTERM, shutting down
[Thu Aug 05 00:12:34 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.2.10-2ubuntu6.4 with Suhosin-Patch configured -- resuming normal operations

```

Do you think it has something to do with the issue I experience?

---

### Post by ruffEdgz on 2010-08-06
That could be the issue with the 'caught SIGTERM' error you are seeing.

When you stop stop the service, do you wait a few seconds before starting it or do you use the 'restart' process to do the stop and starting?

After stopping apache, make sure there aren't any processes running still:
```

ps aux | grep apache

```
If you don't see any, then start it back up and see if you get that error again. If you do see any processes owned by apache, you might want to investigate it further and see if you can just kill it on your own.

During that time, you can still see if the 'indexing' part of apache is or isn't working still.

Hit up this post when you have any further information. Thanks!

---

### Post by ofir_k on 2010-08-06
I restarted the system and everything came back to normal.

Thank to everyone!

---

### Post by TheConformist on 2013-02-10
Sorry to bump this, but I've tried everything listed so far but I'm still being prompted to download the index.php file every time I access my site. (even if I use sites-testing.com/index.php for example)

Has anyone else had and fixed this problem?

---

