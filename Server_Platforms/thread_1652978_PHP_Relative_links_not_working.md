---
title: "PHP Relative links not working"
date: 2010-12-26
forum: Server Platforms
---

### Post by graphikeye on 2010-12-26
Hi all,
I just set up LAMP with PHP. PHP is working fine. I set up a folder with the files. 
Then I modified the config file to this:
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/stefano/public_html/
	<Directory /home/stefano/public_html/>
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/stefano/public_html/>
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

Then I did this: sudo a2dissite default && sudo a2ensite mysite
and restarted the Apache2 service. 

However, relative links just won't work. I am baffled. 
so for example, if i'm trying to add this 
```
<img src="folder/pic1.jpg">
```
it won't render.

---

### Post by aceofspades686 on 2010-12-26
Are you getting any specific errors when you try to access the image directly?  I'm thinking this could be a permissions issue, but without an error I can't really be sure.

If you could, respond with any errors you receive when you try to access the image (not just render it on the page, try going directly to the URL of the image).  Also, just on the offchance the error doesn't give any clues, if you could, run
```
ls -l /home/stefano/public_html
ls -l /home/stefano/public_html/folder
``` (assuming "folder" is the name of your actual image folder) and post the output.  This will make sure and rule out any sort of permissions issues.

---

### Post by graphikeye on 2010-12-26
Hi,
Thanks for getting back to me. When I put in the direct path to the image I get this:

Forbidden

You don't have permission to access /images/homegal/homegal_1.jpg on this server.

```


stefano@stefano-laptop:~$ ls -l public_html/
total 124
drwx------ 2 stefano stefano  4096 2010-12-22 23:58 css
-rwxrwxrwx 1 stefano stefano   201 2010-12-23 00:32 header.php
-rwxrwxrwx 1 stefano stefano   501 2010-12-26 00:09 head.php
-rwxrwxrwx 1 stefano stefano   501 2010-12-26 00:09 head.php~
-rwxrwxrwx 1 stefano stefano 75374 2010-12-24 16:20 homegal_1.jpg
drwx------ 3 stefano stefano  4096 2010-12-24 16:20 images
-rw-r--r-- 1 stefano stefano    54 2010-12-26 00:40 img_test.html
-rw-r--r-- 1 stefano stefano    53 2010-12-26 00:40 img_test.html~
-rwxrwxrwx 1 stefano stefano   903 2010-12-26 00:15 index.php
-rwxrwxrwx 1 stefano stefano   934 2010-12-26 00:15 index.php~
drwx------ 2 stefano stefano  4096 2010-12-22 23:45 js
drwx------ 3 stefano stefano  4096 2010-12-19 14:30 nbproject
-rw-r--r-- 1 stefano stefano    34 2010-12-25 18:40 test.php

```

and

```


stefano@stefano-laptop:~$ ls -l public_html/images/
total 16
-rwxrwxrwx 1 stefano stefano  490 2010-12-23 00:13 body-background-vertical.png
drwx------ 2 stefano stefano 4096 2010-12-24 16:20 homegal
-rwxrwxrwx 1 stefano stefano 6608 2010-12-23 00:36 logo.png

```


Thanks,

---

### Post by aceofspades686 on 2010-12-26
> **graphikeye said:**
> Hi,
Thanks for getting back to me. When I put in the direct path to the image I get this:

Forbidden

You don't have permission to access /images/homegal/homegal_1.jpg on this server.

Called it ;)

Honestly, permission issues are why I don't store any webpages in my home folders (although a perfectly normal thing to do mind you, just not something I prefer).  That being said, there are a few things I can help you out with to get everything up and running.

> **graphikeye said:**
> ```


stefano@stefano-laptop:~$ ls -l public_html/
total 124
drwx------ 2 stefano stefano  4096 2010-12-22 23:58 css
...
drwx------ 3 stefano stefano  4096 2010-12-24 16:20 images
...
drwx------ 2 stefano stefano  4096 2010-12-22 23:45 js
drwx------ 3 stefano stefano  4096 2010-12-19 14:30 nbproject
...

```

and

```


stefano@stefano-laptop:~$ ls -l public_html/images/
total 16
...
drwx------ 2 stefano stefano 4096 2010-12-24 16:20 homegal
...

```


Thanks,
(I removed the ones that for the most part aren't relevant when looking at this).

Before I get started, I would like to note that I am not an expert on *nix permissions, and the advice I'm about to dispense is only from my own personal experiences.

As it stands, you have two primary problems that I can see offhand:
[LIST=1]
[*]Your permissions do not allow any users besides you to browse the folder.
[*]www-data (the user apache runs as) can not access those directories since it is neither the owner, nor a group member
[/LIST]

The first one, while chmod 0700 is typically a good idea on home directories, when it comes to websites it can cause some problems, particularly since you need www-data to be able to read/write these files.  Personally, what I would do in this situation is give owner and group rwx permissions, and give others r_x permissions on all files and folders.  (Side note: You may be able to take all permissions away from "others" but I seem to remember that causing some problems for me in the past, so worth a try, but it could break things).

From there, you either make www-data the owner and leave your personal group as the group or keep yourself as the owner and change the group to www-data.  I prefer to do the latter if its going to be located in my personal home folder.  Also, you may not need Apache to be able to write to these folders, in which case, having it as the group makes more sense.

```

sudo chgrp -R www-data /home/stefano/public_html
sudo chmod -R 775 /home/stefano/public_html
```

alternatively, if you don't need apache to be able to write to the directories:
```

sudo chgrp -R www-data /home/stefano/public_html
sudo chmod -R 755 /home/stefano/public_html
```

Just to reiterate, I am not an expert, and I'm running off memory because I don't have my server in front of me, but I think either one of these should fix this issue for you.  A quick tip however if you don't mind is to move the public_html folder out of your home folder (assuming you can) and into a folder designation for this.  I use /home/www/<domain name of site>/public_html/ because this way you can keep it separate from your personal documents.

Hope this fixes everything for you, just reply and let me know if this doesn't work for some reason and we'll keep digging.

---

