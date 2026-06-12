---
title: "Apache 2 quick question."
date: 2010-05-04
forum: Server Platforms
---

### Post by DragoshDX on 2010-05-04
Hello, I am new to Ubuntu. 
I recently had the job of administrating an ubuntu server (9.10 I believe) dropped on me.

The server root I have is /var/www, I assume that's where ubuntu default instalation puts it.

There were two folders there that can be seen from the outside, I created a new folder with sudo privileges, and placed an xml file there, but I can't see it from the internet. If I move it in one of the existing folders I can see it just fine.

My question is how do I make apache serve all the new folders I create and all the files in them by direct link.

NOTE: Folders should not display their index tree if an index.html/php is missing but should allow direct acces to files/folders inside them by direct URL address.

Thank you.

---

### Post by tumandro on 2010-05-04
Do you have the correct permissions on the file?

---

### Post by DragoshDX on 2010-05-04
Well I believe /var/www owner is root but ubuntu doesn't have any root acount.

Should I change permisions to read for everyone? 
How do I do that?

---

### Post by cdenley on 2010-05-04
> **DragoshDX said:**
> Well I believe /var/www owner is root but ubuntu doesn't have any root acount.

Should I change permisions to read for everyone? 
How do I do that?

There is a root user. It doesn't have a password, though, so you can't authenticate as root. Anything done with "sudo" will be done with the root user, though.

Documents and directories served by apache need to be readable by the user www-data. This is usually done by making them world-readable.
```

sudo chmod -R o+rwX /var/www/newfolder

```
What do your site configurations look like?
```

sudo cat /etc/apache2/sites-enabled/*

```

If you don't want directory listings, don't enable it. Make sure "Indexes" isn't listed on any "Options" directive. If it is, remove it.
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options **[COLOR="Red"]Indexes[/COLOR]** FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
</VirtualHost>

```

---

### Post by DragoshDX on 2010-05-04
Thank you!

I will try changing permissions first thing in the morning as I get to work.
And display the output for cat.

---

### Post by sonik88 on 2010-05-04
Two tips if I may: Try to send the files ot the server over ftp. There is a good chance the previous administrator had set it right so the files you upload are immediatelly visible. Also try the more command instead of cat.

Good Luck

---

### Post by cdenley on 2010-05-04
> **sonik88 said:**
> Two tips if I may: Try to send the files ot the server over ftp. There is a good chance the previous administrator had set it right so the files you upload are immediatelly visible. Also try the more command instead of cat.

Good Luck

If the server is configured to allow files to be uploaded to /var/www via FTP, then my tip is to remove it, or at least ensure it isn't accessible from the internet. Unless you use SSL encryption, this is very insecure. Also, the more command isn't very useful for copying/pasting entire configuration files to this thread.

---

### Post by tgalati4 on 2010-05-04
Also, apache2 wants all files below /var/www to be www-data:www-data in ownership as apache2 runs as user www-data.  This was stated previously and the command to do that:

sudo chown -R www-data:www-data /var/www/myserverdata

Any .htacess files should remain root ownership.

---

### Post by Vegan on 2010-05-04
All you need to do is....

sudo chmod -R 755 /var/www/

you do not need to change the ownership

---

### Post by cdenley on 2010-05-04
> **tgalati4 said:**
> Also, apache2 wants all files below /var/www to be www-data:www-data in ownership as apache2 runs as user www-data.  This was stated previously and the command to do that:

sudo chown -R www-data:www-data /var/www/myserverdata

Any .htacess files should remain root ownership.

No. Unless there are special circumstances which require this, it is safer to leave it owned by root. If your web applications or server gets compromised, you don't want the contents of /var/www getting altered maliciously. Apache only needs to read content to serve it, not modify it.
```

sudo chmod -R o+rwX /var/www

```

---

### Post by tgalati4 on 2010-05-04
If you are running drupal, sugarcrm, or other php-based services, then they recommend www-data ownership because the dynamic page content can't be created otherwise.  But you are correct, everything is more secure with root.

You just may not be able to view the page.

---

### Post by cdenley on 2010-05-04
> **tgalati4 said:**
> If you are running drupal, sugarcrm, or other php-based services, then they recommend www-data ownership because the dynamic page content can't be created otherwise.

Those are the special circumstances I was referring to. Since a self-altering web application was not mentioned, I would not suggest giving apache permission to modify the files it serves.

> **tgalati4 said:**
> 
You just may not be able to view the page.

If permissions are set correctly, you can view content just fine.

---

### Post by DragoshDX on 2010-05-05
Hello,
I tried both the chmod commands however none did the job. Though I believe they were the same thing as the man page indicated.

The page isn't even viewable on the server itself.

This is the output from the cat command.

```

$ sudo cat /etc/apache2/sites-enabled/*
# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
    Options Indexes FollowSymLinks
    DirectoryIndex index.php

    <IfModule mod_php5.c>
        AddType application/x-httpd-php .php

        php_flag magic_quotes_gpc Off
        php_flag track_vars On
        php_flag register_globals Off
        php_value include_path .
    </IfModule>

</Directory>

# Authorize for setup
<Directory /usr/share/phpmyadmin/setup>
    <IfModule mod_authn_file.c>
    AuthType Basic
    AuthName "phpMyAdmin Setup"
    AuthUserFile /etc/phpmyadmin/htpasswd.setup
    </IfModule>
    Require valid-user
</Directory>

# Disallow web access to directories that don't need it
<Directory /usr/share/phpmyadmin/libraries>
    Order Deny,Allow
    Deny from All
</Directory>
<Directory /usr/share/phpmyadmin/setup/lib>
    Order Deny,Allow
    Deny from All
</Directory>

<VirtualHost *:80>

    ServerName lzcpdasfs17.unitbv.ro 
    DocumentRoot /var/www/tags

    WSGIScriptAlias / /home/tagserver/tagserver/web/django/witag/django.wsgi
    Alias /static /home/tagserver/tagserver/web/django/witag/static
    Alias /admin/media/ /usr/share/pyshared/django/contrib/admin/media/

Alias /tag4mdemo /var/www/tag4mdemo

    LogLevel warn
    ErrorLog /var/log/apache2/tags-error.log
    CustomLog /var/log/apache2/tags.log combined
</VirtualHost>

```


I also changed the owner to www-data as well and still nothing. 
Anything else I should check?

Thank you.

---

### Post by cdenley on 2010-05-05
Your DocumentRoot is not /var/www! You need to edit your vhost configuration in /etc/apache2/sites-available. I think this will give you what you want.
```

<VirtualHost *:80>
    ServerName lzcpdasfs17.unitbv.ro 
    DocumentRoot /var/www/tags
    [B]<Directory /var/www/newfolder>
        Order Deny,Allow
        Allow From All
        Options -Indexes
    </Directory>
    Alias /newfolder /var/www/newfolder[/B]

    WSGIScriptAlias / /home/tagserver/tagserver/web/django/witag/django.wsgi
    Alias /static /home/tagserver/tagserver/web/django/witag/static
    Alias /admin/media/ /usr/share/pyshared/django/contrib/admin/media/

Alias /tag4mdemo /var/www/tag4mdemo

    LogLevel warn
    ErrorLog /var/log/apache2/tags-error.log
    CustomLog /var/log/apache2/tags.log combined
</VirtualHost>

```

then reload apache
```

sudo /etc/init.d/apache2 reload

```

---

### Post by terazen on 2010-05-05
DocumentRoot is set to /var/www/tags.  You could edit this file or create a new site depending on what you want to do.  How do you want the site to work differently than it does now?

---

### Post by DragoshDX on 2010-05-05
So every time I add a new folder in the sites-available file. 
Say for example:
/www/var/temp 

Only then will /temp be available from the outside? 

And that means every time I add another folder I need to edit de sites-available file? 
I am actually pleased with the ideea, because that means nobody will mess up my www root folder. 


I think I understand now. I'll try it when I get to work.

Thank you!

---

### Post by cdenley on 2010-05-05
> **DragoshDX said:**
> So every time I add a new folder in the sites-available file. 
Say for example:
/www/var/temp 

Only then will /temp be available from the outside? 

And that means every time I add another folder I need to edit de sites-available file? 
I am actually pleased with the ideea, because that means nobody will mess up my www root folder. 


I think I understand now. I'll try it when I get to work.

Thank you!

Based on your current configuration.

---

### Post by sgrrr on 2010-05-05
> **DragoshDX said:**
> So every time I add a new folder in the sites-available file. 
Say for example:
/www/var/temp 

Only then will /temp be available from the outside? 

And that means every time I add another folder I need to edit de sites-available file? 
I am actually pleased with the ideea, because that means nobody will mess up my www root folder. 


I think I understand now. I'll try it when I get to work.

Thank you!

Could you explain what you mean by that? I'm afraid you might be running in a dead end. There are several possibilities to dis/-allow access on contents via apache

---

### Post by DragoshDX on 2010-05-05
Well, as I understand it.

To have a valid folder in the /var/www directory I firstly would need to declare it in the availabe-sites file, which is ok, every time I want something new I just edit that file. 

Also, as I've been reading I can declare a folder anywhere on the filesystem and then give it an alias that points to /var/www/folder-in-filesystem, correct?

---

### Post by sgrrr on 2010-05-06
> **DragoshDX said:**
> Well, as I understand it.

To have a valid folder in the /var/www directory I firstly would need to declare it in the availabe-sites file, which is ok, every time I want something new I just edit that file. 

Also, as I've been reading I can declare a folder anywhere on the filesystem and then give it an alias that points to /var/www/folder-in-filesystem, correct?

This depends on which directory you choose as document root. If it's /var/www you should probably be able to access any directory underneath by extending the URL while Indexing is enabled or there is a valid index.html/.php/.younameit file within the child directory. You can use access-restrictions like within a .htaccess file.

I wouldn't recomment spreading you webcontents across the whole filesystem. You could use symbolic links within /var/www that point to other directories, but if possible, put the content where it belongs.

---

### Post by DragoshDX on 2010-05-06
Well clearly I wouldn't spread web files all over the computer. But I was thinking theoretically.

I haven't been able to test the new suggestions because of other work stuff, but I'll post my result as soon as I get around to managing the server.

I checked and I noticed that entering a directory with index.php/html files does indeed display the folder index. 
I know how to solve the problem with .htaccess, but should I use .htaccess to deny indexing or the sites-available file? Or is it the same thing?

---

### Post by DragoshDX on 2010-05-11
Solved.

I actually had to add something like 

Alias /newfolder /var/www/newfolder on of the sites available files.

Further on I may try to deny access to indexes with the <directory> statements or .htacces, but for now this solution is satisfying.

Thank you all!

---

### Post by cdenley on 2010-05-11
> **DragoshDX said:**
> Solved.

I actually had to add something like 

Alias /newfolder /var/www/newfolder on of the sites available files.

Further on I may try to deny access to indexes with the <directory> statements or .htacces, but for now this solution is satisfying.

Thank you all!

What do you mean actually? That is exactly what I suggested.

---

### Post by DragoshDX on 2010-05-11
I know. But you also said I should modify the <directory> statement, or I probably misunderstood because you also said how to disable indexing... 

Thank you.

(P.S. Not a native english speaker,)

---

### Post by cdenley on 2010-05-11
> **DragoshDX said:**
> I know. But you also said I should modify the <directory> statement, or I probably misunderstood because you also said how to disable indexing... 

Thank you.

(P.S. Not a native english speaker,)

Yes, if you want to disable indexes, you need a directory statement somewhere. Also, it is best to disallow access to everywhere, then allow the directories you wish to serve. Since you didn't disallow everywhere in your vhost configuration, you don't need to specifically allow access to your new directory, but I thought I would suggest it in case you decide to fix your vhost configuration and to encourage proper configuration. After all, allowing access to your new directory couldn't hurt.

---

