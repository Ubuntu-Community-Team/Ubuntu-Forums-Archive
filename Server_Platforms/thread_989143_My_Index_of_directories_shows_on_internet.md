---
title: "My Index of directories shows on internet?"
date: 2008-11-21
forum: Server Platforms
---

### Post by mrmyers on 2008-11-21
This is what is showing and I can't seem to get this fixed myself:

Index of /
[ICO]	Name	Last modified	Size	Description
[DIR]	ioncube/	15-Nov-2008 20:35 	-
[DIR]	kazoops/	15-Nov-2008 20:18 	-
[DIR]	kazoops2008/	15-Nov-2008 16:24 	-
[DIR]	kazoops2009/	16-Nov-2008 12:51 	-
[DIR]	lost+found/	13-Nov-2008 19:03 	-
[ ]	test	14-Nov-2008 18:38 	0
[DIR]	webalizer/	16-Nov-2008 00:47 	- 

Apaches shows /var/www.kazoops2009/web

Anyone have any suggestions? Please!

---

### Post by hictio on 2008-11-21
I'm not clear.
You don't want your directories to show? Or you don't care about showing directories, but you are seeing content you are not expecting?

---

### Post by mrmyers on 2008-11-21
No, I expect index.php to load the Home page of my website but instead I get a page that lists all of the directories in my /var/www folder

Site is [http://kazoops.com](http://kazoops.com)

---

### Post by hictio on 2008-11-21
Then, I see a problem, I don't see any index.php file on that directory?
Are you sure you are placing the file on the right directory on your server?
What are the 'DocumentRoot' and the 'Directory' values on your config file?

---

### Post by mrmyers on 2008-11-21
The index file exists under: /var/www/kazoops2009/web/index.php

and on the Internet at [http://kazoops.com/kazoops2009/web/](http://kazoops.com/kazoops2009/web/)

In other words my document options in Apache2 are not resolving correctly to the web.  I have it setup as /var/www/kazopps2009/web and directory indexing has index.php entered.

When I go to [http://kazoops.com/kazoops2009/web/](http://kazoops.com/kazoops2009/web/)  I get a jumbled page and then when I click on a menu item it will fo to a direct link, for example if I click on menue item Blogs forefox will go to: [http://kazoops.com/blogs/](http://kazoops.com/blogs/) and get this error:

Not Found

The requested URL /blogs/ was not found on this server.
Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch Server at kazoops.com Port 80

Obviously I have some option set up incorrectly.

---

### Post by hictio on 2008-11-21
> **mrmyers said:**
> The index file exists under: /var/www/kazoops2009/web/index.php

and on the Internet at [http://kazoops.com/kazoops2009/web/](http://kazoops.com/kazoops2009/web/)

In other words my document options in Apache2 are not resolving correctly to the web.  I have it setup as /var/www/kazopps2009/web and directory indexing has index.php entered.

When I go to [http://kazoops.com/kazoops2009/web/](http://kazoops.com/kazoops2009/web/)  I get a jumbled page and then when I click on a menu item it will fo to a direct link, for example if I click on menue item Blogs forefox will go to: [http://kazoops.com/blogs/](http://kazoops.com/blogs/) and get this error:

Not Found

The requested URL /blogs/ was not found on this server.
Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch Server at kazoops.com Port 80

Obviously I have some option set up incorrectly.

That's what I'm telling you.
Check on the Apache configuration file what the directives 'DocumentRoot' and 'Directory' are pointing.
First, let's make sure you are placing that 'index.php' file in the right spot.

---

### Post by cdenley on 2008-11-21
Here is what you need to do:
```

sudo nano /etc/apache2/sites-available/default

```
Replace the line
```

DocumentRoot /var/www/

```
with
```

DocumentRoot /var/www/kazoops2009/web/

```
save it, then run
```

sudo /etc/init.d/apache2 reload

```

---

### Post by mrmyers on 2008-11-21
Thank you but I have one more question!

By changing this, don't I limit myself to just one web site on this server?

---

### Post by cdenley on 2008-11-21
> **mrmyers said:**
> Thank you but I have one more question!

By changing this, don't I limit myself to just one web site on this server?

No. If you want to make another site (virtual host):
```

sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/newsite
sudo nano /etc/apache2/sites-available/newsite

```
above the "DocumentRoot" option, add something like
```

ServerName mysite.com
ServerAlias www.mysite.com

```
Make sure there is no "NameVirtualHost" line at the top. Change "DocumentRoot" and anything else you want.
Then enable it, and reload:
```

sudo a2ensite newsite
sudo /etc/init.d/apache2 reload

```

---

### Post by hictio on 2008-11-21
> **mrmyers said:**
> Thank you but I have one more question!

By changing this, don't I limit myself to just one web site on this server?

You can use Virtual Servers, if those have a valid hostname, but, in a way, yes, the contents of the '/var/www/kazoops2009/web/' directory will be, the "site" for that server.
But, you can set as many virtual servers as you box can handle without melting.

---

### Post by mrmyers on 2008-11-21
Thank you.  You have been a great help and I got all of that working fine.  Our plan is to not host any other site on this server because of band width issues with all of the video files we have. I have another ubuntu server that hosts our other sites.

All home based and self taught so I am ignorant on problems like this.

Thanks again.

---

