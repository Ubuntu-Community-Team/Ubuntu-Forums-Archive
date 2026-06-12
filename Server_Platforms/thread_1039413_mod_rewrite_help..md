---
title: "mod_rewrite help."
date: 2009-01-14
forum: Server Platforms
---

### Post by Kismet on 2009-01-14
I cannot get mod_rewrite to work. 
I have enabled it through 'sudo a2enmod rewrite'.

Under /mods-enabled/ there is 'rewrite.load'
contents
```
LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so
```


Here is a snippet of my /sites-enabled/ file

```
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
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
		RewriteRule ^/bob$ /temp1/temp1/temp2

	</Directory>
```

under /var/www/ I have temp1/temp1/temp2 directories set up just to try and test this.

I've tried putting the rewrite rule just under the virtual host, in a .htaccess file, in the httpd.conf. Nothing works.

grepping the access.log and error.log for '[Rr]ewrite' produces no results. There are no mod_rewrite logs.

It looks to me like the module is never actually getting loaded. But who knows.

I am completely frustated and lost, any suggestions????

Thanks for any insight!

---

### Post by spiderbatdad on 2009-01-14
[http://forum.modrewrite.com/viewforum.php?f=12](http://forum.modrewrite.com/viewforum.php?f=12)
The stickys on this page contain all the basics.

---

