---
title: "Apache 2 .htaccess Troubles"
date: 2009-05-03
forum: Server Platforms
---

### Post by jfmanamtr on 2009-05-03
I am running Ubuntu Server 8.10 using Apache Apache 2.2.9. I am trying to use an .htaccess file to prevent people from browsing the folders under the document root, but have thus far had no luck getting this to work.  I have the .htaccess in the root directory for my web sites with the following line in it:

```
Options -Indexes
```

I also added the following code to my apache2.conf 

```

<Directory "/webroot">
        AllowOverride All
</Directory>

```

After I restart Apache, I remove the temp index file & go to my site, but I can still view the folder listings. Any ideas on what is going on?

~John

---

### Post by tux-helper on 2009-05-03
Although it sounds like what you're doing should work, this post:

[http://www.phpfreaks.com/forums/index.php?topic=222218.0](http://www.phpfreaks.com/forums/index.php?topic=222218.0)

suggests adding 'IndexIgnore *' to your .htaccess file - worth a try

---

### Post by jfmanamtr on 2009-05-03
Ok. so I added the following line to my .htaccess file:
 
```
IndexIgnore *
```
 
And it still doesn't seem to be working. If I remove the index.html file from the root directory, it still lists all the folders & files in that directory. Any other ideas because I am completely out of clues as to why this won't work. Thanks for all the help thus far!
 
~John

---

### Post by bluefrog on 2009-05-04
Do your apache a favor, don't use htaccess.

In the directory section of your virtualhost add
IndexIgnore *

You must at least reload Apache2

so basically /etc/apache2/sites-available/site

<VirtualHost *:80>
	ServerAdmin [email]webmaster@site.com[/email]
	ServerName site.com
	ServerAlias *.site.com
	DocumentRoot /var/www/site

	<Directory /var/www/site/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None 
		Order allow,deny
		allow from all
		Include /etc/apache2/sites-available/security
		IndexIgnore *
	</Directory>
</VirtualHost>

---

