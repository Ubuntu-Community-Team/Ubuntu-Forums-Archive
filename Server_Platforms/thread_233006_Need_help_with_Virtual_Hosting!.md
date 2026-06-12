---
title: "Need help with Virtual Hosting!"
date: 2006-08-09
forum: Server Platforms
---

### Post by zoon_unit on 2006-08-09
I'm trying to set up a virtual host on my Ubuntu LAMP install.

1) I went to etc/apache2/sites-available and copied the default config file, naming it the name of my new virtual site, which for this post I'll call mynewsite.  (this is per the Ubuntu documentation)

2) Then I changed the following settings in the new file to match mynewsite:  (first few lines of the file)

```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/drupal
	ServerName www.mynewsite.com
	ServerAlias *.mynewsite.com mynewsite.com

```

3) Then I "activate" the new site by typing:

```
sudo a2ensite mynewsite
```

I get a message back saying the new site is activated and to reload the server with:

```
/etc/init.d/apache2 reload
```

But when this runs, I get the following message:

```
[warn] NameVirtualHost *:0 has no VirtualHosts
```

Most importantly, my new virtual host doesn't work!!

Anybody know what I'm doing wrong?  Is there anything else I need to do to activate this virtual host??

---

### Post by jordans on 2006-08-26
I know this post has been out for a while but i think i can help here is what your sites-availble should look like.

```
NameVirtualHost *
<VirtualHost *:80>
  ServerName secondwebsite.com
  ServerAlias [www.secondwebsite.com]("http://www.secondwebsite.com/")
  DocumentRoot /var/www/secondwebsite
  CustomLog /var/log/apache2/sitename.com-access.log combined
  ErrorLog /var/log/apache2/sitename.com-error.log
</VirtualHost>
<VirtualHost *:80>
  ServerName firstwebsite.com
  ServerAlias [www.firstwebsite.com]("http://www.vashontechsupport.com/")
  DocumentRoot /var/www/firstwebsite/
  CustomLog /var/log/apache2/sitename.com-access.log combined
  ErrorLog /var/log/apache2/sitename.com-error.log
</VirtualHost>
```Easy enough. So far this has worked for everyone.

---

