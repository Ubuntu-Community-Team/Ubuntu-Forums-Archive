---
title: "How to disable directory indexing in apache2??"
date: 2006-08-12
forum: Server Platforms
---

### Post by chrisfay on 2006-08-12
How do I disable directory indexing in Apache2? I removed the options+indexing in my virtual host but that didn't work.

Anyone know what to remove or add in my config file?

---

### Post by scxtt on 2006-08-12
did you restart apache after you did that?

---

### Post by chrisfay on 2006-08-12
yes

---

### Post by scxtt on 2006-08-12
well, one way is to chmod 701 your public_html directory (or any directory, i imagine) ... or put a blank index.html file in each one ...

---

### Post by chrisfay on 2006-08-12
I thought there was a way to block the indexing option completely.

---

### Post by scxtt on 2006-08-12
all i had to do, aside from what i mentioned above, was remove **Indexes** from my **Options** ... i'm not using anything virtual, this is in my public_html setup ...

---

### Post by chrisfay on 2006-08-12
I wonder if it's different since I'm using virtual hosts. Maybe something in the sites-enabled config file within the host setup itself. 

Interesting enough, I tried to add this to my apache2.conf file:

<Directory /> 
Order Deny,Allow 
Deny from all 
</Directory>

It didn't block anything to my three sites. But, when I did it within the virtual host <Directory> in sites-enabled it blocked access to my site. 

Is this an indication that directives must be made within the virtual config and not in apache2.conf?

---

### Post by scxtt on 2006-08-12
>> Is this an indication that directives must be made within the virtual config and not in apache2.conf?

that's how it seems to me ...

---

### Post by chrisfay on 2006-08-12
Someone has to know how to disable this. I can't imagine everyone running apache has directory indexing enabled for virtual hosts....

---

### Post by Kurt` on 2006-08-12
Directory listings?

Put "Options -Indexes" into a .htaccess file in the directory, or into a <Directory> section for it. e.g.

<Directory "/var/www">
Options -Indexes
</Directory>

Unless you override it in another folder, it will apply to ALL subfolders as well.

Also, don't add stuff to apache2.conf. If you're using the default setup, add it to /etc/apache2/sites-available/000-default (it's either 000-default, or default, I can't remember).

Oh, and don't restart apache when you change a configuration setting. -_- Use # sudo /etc/init.d/apache2 reload

---

### Post by chrisfay on 2006-08-12
> Put "Options -Indexes" into a .htaccess file in the directory, or into a <Directory> section for it. e.g.

<Directory "/var/www">
Options -Indexes
</Directory>

Perfect, that worked! You have to add the "Options -Indexes" within each virtual host or it won't apply to all of them. At least it wouldn't for me.

---

### Post by Kurt` on 2006-08-12
.htaccess is a little more flexible (and you don't have to reload apache every time you change something), but adding it to the config file for the VirtualHost consolidates all of your changes.

Either will work, as they both do the same thing.

If you have anymore problems, feel free to post. :)

---

### Post by webdesigncompany on 2008-01-03
Hey you can use **Options -Indexes** without the directory name too

[B]
Instead of[/B]
<Directory "/var/www">
Options -Indexes
</Directory>

go to directory **/var/www** and create .htaccess file with Options -Indexes inside and you are done :)

---

### Post by scottlindner on 2008-02-02
How do you really disable directory indexing?  I have tried adding Options -Indexes or removing all Options altogether from my Apache2 configuration and directory indexing is still on.  I have added Options -Indexes to the main apache2.conf file, the default file, and all virtual host config files all at the same time and directory indexing is still on.  There must be a way to turn this off globally with some form of supreme authority that nothing no matter what can override it.  How is this done?

Cheers,
Scott

---

### Post by scottlindner on 2008-02-02
> **webdesigncompany said:**
> Hey you can use **Options -Indexes** without the directory name too

[B]
Instead of[/B]
<Directory "/var/www">
Options -Indexes
</Directory>

go to directory **/var/www** and create .htaccess file with Options -Indexes inside and you are done :)

I have tried this as well and directory indexing still is on.  To verify it isn't a browser caching problem I have tried multiple browsers, multiple computers, rebooting the server, shutting down all equipment including routes and hubs at the same time, even shutting off my cable modem in the hopes of getting this flippin directory indexing turned off.  How in the world do you do this?

Regards,
scott

---

### Post by scxtt on 2008-02-02
for anyone having problems ...

i was able to disable indexing by doing the following:
```
:> head -20 /etc/apache2/sites-enabled/000-default
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                [COLOR="Red"]Options **-Indexes** FollowSymLinks MultiViews[/COLOR]
```

---

### Post by scottlindner on 2008-02-02
I don't know why it always happens like this.  I've been struggling with this for weeks.  Two minutes after posting I figured it out.  I had two modules that were setting the option globally.  That's why it seemed like no matter what I did it seemed like something globally was enabling it even though I couldn't find it.  I suggest for everyone having this trouble to check your /etc/apache2/mods-available/ directory for anything that might be setting Indexes.  I had two modules that enabled it; alias.conf and userdir.conf  After commenting out the Indexes in both of those my troubles went away.

Cheers,
Scott

---

