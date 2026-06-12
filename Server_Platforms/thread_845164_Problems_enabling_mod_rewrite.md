---
title: "Problems enabling mod_rewrite"
date: 2008-06-30
forum: Server Platforms
---

### Post by zephyrcat on 2008-06-30
In order to get clean URLs to work in Drupal on LAMP, I am trying to enable mod_rewrite in Apache. So far, this is what I have done:

```
apache2ctl -t -D DUMP_MODULES
```
This does not return mod_rewrite, although it returns lots of other modules.
```
sudo a2enmod rewrite
```
This returns: This module is already enabled!

I added this code to my /etc/apache2/apache2.conf:
```
<IfModule mod_rewrite.c>
RewriteEngine On
</IfModule>
```

I have changed this part of my /etc/apache2/sites-enabled/000-default:
```
<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		**AllowOverride None**
		Order allow,deny
		allow from all
	</Directory>
```
to this:
```
<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		**AllowOverride all**
		Order allow,deny
		allow from all
	</Directory>
```

In /var/www/lldrupal/.htaccess (lldrupal being the name of my test Drupal site), there is already this section (some comments have been removed, because they are very long):
```
<IfModule mod_rewrite.c>
  RewriteEngine on


  # Rewrite URLs of the form 'index.php?q=x'.
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteRule ^(.*)$ index.php?q=$1 [L,QSA]
</IfModule>
```

And I have restarted Apache many times. Still, though, when I try to enable clean URLs in Drupal I get this error:
```
Your system configuration does not currently support this feature. The handbook page on Clean URLs has additional troubleshooting information.
```

Any idea how I can get this working? I suspect this is an Apache-related problem, but if you think I should take this question to the Drupal forum, I can do that, too.

Thanks!

---

### Post by mrpeenut24 on 2008-06-30
Looks to me like you're doing everything right.  When you run the dump_modules, does it show rewrite_module?  That's what it usually shows as.  Also, I would suggest against editing the apache2.conf file, as this can get overwritten when you update.  Instead, I would put it in httpd.conf or /etc/apache2/sites-available/default under the Directory directive you're working in.

If it still doesn't work, I'd take it to the drupal forum and see what they know.  Because this looks correct to me.

---

### Post by osjak on 2008-06-30
zephyrcat, I would join mrpeenut24 here - your Apache config seems correct. 

I doubt that Drupal is sofisticated enough to verify errors in your Apache config, it probably checks for someething simple and makes a desision on that one fact if your host can run short URL's or not. I would suggest the same thing - ask on Drupal support forum for this.

BTW, the way you check loaded modules never worked correctly for me. I have found out phpinfo() function gives far better results. Try it, and I bet you will see your mod_rewrite loaded.

---

### Post by zephyrcat on 2008-06-30
Alright, I posted the question to the Drupal forums:

[http://drupal.org/node/276950](http://drupal.org/node/276950)

Also, no there is nothing about rewrite in the output of the apache2ctl command and I moved my changes to the apache2.conf to the httpd.conf without any luck.

---

### Post by mrpeenut24 on 2008-07-01
Hmm.  In this particular case, I don't think it would really matter where it is, and you might not even need it at all since you're turning it on in the .htaccess file.  Do what osjak said and try phpinfo.  Make a file "test.php" and inside put the following:

```

<?php
phpinfo();
?>

```

Then navigate to this page in a browser and see what mods are enabled.

---

### Post by zephyrcat on 2008-07-01
Thanks. I tried that, but it is not listed in the loaded modules.

---

### Post by mrpeenut24 on 2008-07-01
Hmm...

Try this:

```

sudo a2dismod rewrite
sudo /etc/init.d/apache2 restart
sudo a2enmod rewrite
sudo /etc/init.d/apache2 restart

```

Then check phpinfo() again.

---

### Post by zephyrcat on 2008-07-01
Thanks, but still no luck.

---

### Post by osjak on 2008-07-01
I reread your first post and don't see you showing showing mod_rewrite was actually scheduled to load at Apache start. Please post the outcome of this:

```
cat /etc/apache2/mods-enabled/rewrite.load
```

---

### Post by zephyrcat on 2008-07-01
All I get is a blank line.

---

### Post by osjak on 2008-07-01
OK, your mod_rewrite doesn't load with apache restart. Run this:

```
sudo echo "LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so" > /etc/apache2/mods-available/rewrite.load
cat /etc/apache2/mods-enabled/rewrite.load
```

Make sure the last command results in:
```
LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so
```
back to you.

Now restart Apache and check if mod_rewrite working.

---

### Post by zephyrcat on 2008-07-01
Thanks so much! That worked and clean URLs are enabled!

---

### Post by mrpeenut24 on 2008-07-02
Hmm.  That's weird.  Usually that's what a2enmod does, doesn't it?

Anyway I'm glad it all got worked out!

---

### Post by osjak on 2008-07-02
> **zephyrcat said:**
> Thanks so much! That worked and clean URLs are enabled!
You are welcome. I'm also glad this unusual issue got solved :)

---

### Post by ceabaird on 2008-08-14
Osjak,

I've been beating my head out for over a week trying to get clean urls set up in drupal. I followed the suggestions here, and voila!

Clean urls are now enabled.

Thanks.

---

### Post by megladon on 2008-08-21
I'm trying to get clean urls to work too. I get the same error message. Here's an additional issue I'm having. my /etc/apache2/sites-available/default is blank. Just an empty file. What should be in there? Is there a way I can get a copy of another person's file to replace mine with?

---

### Post by megladon on 2008-08-21
my /etc/apache2/apache2.conf is blank too. There's nothing in the file.

---

### Post by megladon on 2008-08-21
Nevermind.......they're not empty. forgot Sudo.    lol

---

### Post by dazmcg on 2008-08-21
I'm having a similar problem with Drupal.

my output from 'apache2ctl -t -D DUMP_MODULES' does not have any mod_rewrite module listed, BUT it /does/ have this line:
rewrite_module (shared)

also in phpinfo lists mod_rewrite as a loaded module in apache2handler. So it should be working right? Yet drupal still says it's not enabled.

help appreciated

daz

---

