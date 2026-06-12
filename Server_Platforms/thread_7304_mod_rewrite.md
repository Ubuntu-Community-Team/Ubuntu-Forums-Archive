---
title: "mod_rewrite"
date: 2004-12-05
forum: Server Platforms
---

### Post by Crisp on 2004-12-05
Hi
 
 I installed Apache/MySQL/PHP4 and it's all working fine.  However, I now have a need to enable/install mod_rewrite.  This is the first real experience I've had setting up Apache, usually I just use a hosted environment.  
 
 Could someone walk me through enabling or installing mod_rewrite please?
 
 Thanks
 
 -Crisp

---

### Post by Hikaru79 on 2004-12-06
A quick google search turned this up: [http://httpd.apache.org/docs/mod/mod_rewrite.html](http://httpd.apache.org/docs/mod/mod_rewrite.html)

If that's not comprehensive enough, I don't know what is ^ ^;;

---

### Post by Crisp on 2004-12-06
[QUOTE=Hikaru79]A quick google search turned this up: [http://httpd.apache.org/docs/mod/mod_rewrite.html](http://httpd.apache.org/docs/mod/mod_rewrite.html)

If that's not comprehensive enough, I don't know what is ^ ^;;[/QUOTE]
 Yeah I've been there, the problem is it's a little *too* comprehensive, I just want a quick and easy setup.  I don't need the ins and outs of every last part of it and how to use it.

-Crisp

---

### Post by Levander on 2005-03-08
[QUOTE=Crisp]Yeah I've been there, the problem is it's a little *too* comprehensive, I just want a quick and easy setup.  I don't need the ins and outs of every last part of it and how to use it.

-Crisp[/QUOTE]

Realize this post is a little old, but may help if I answer it?

sudo a2enmod rewrite

Adds a .load file to /etc/apache2/mods-enabled/ that loads the module.

Then, you have to make sure that RewriteEngine on is somewhere in your Apache configuration.  WordPress 1.5 inserts the RewriteEngine directive in the .htaccess file in the directory  where WordPress is installed.  I'm sure in apache2.conf would be fine to.  Looks something like this:

<IfModule mod_rewrite.c>
RewriteEgine On
</IfModule>

---

### Post by invalid on 2005-09-06
Again, a reply to an old post, but this has helped me out - and I just wanted to correct a typo in the last reply, incase someone is not able to determine the error printed by apache..

It should be:

```
<IfModule mod_rewrite.c>
RewriteEngine On
</IfModule>
```

Cheers,
Cb

---

### Post by neocon2005 on 2005-09-20
Thank you very much for the answer. Worked very well for me. Goes to show that even though the reply was delayed, it can still be useful for people searching for information at a much later date - people like me!!!

---

### Post by DDM on 2005-09-24
Just letting people know that this thread was really useful, I had been trying to enable mod_rewrite for gallery2 for a while now, the apache doc was way too comprehensive for my tastes.

---

### Post by markthecarp on 2005-10-25
[QUOTE=Levander]Realize this post is a little old, but may help if I answer it?

sudo a2enmod rewrite

Adds a .load file to /etc/apache2/mods-enabled/ that loads the module.
[/QUOTE]
This worked for me. It created the file /etc/apache2/mods-enabled/rewrite.load which turns out to be a sym link.
```
mark@tuna:/usr/share/gallery/css$ ll /etc/apache2/mods-enabled/rewrite.load
lrwxrwxrwx  1 root root 40 2005-10-24 21:03 /etc/apache2/mods-enabled/rewrite.load -> /etc/apache2/mods-available/rewrite.load
```

> Then, you have to make sure that RewriteEngine on is somewhere in your Apache configuration.  WordPress 1.5 inserts the RewriteEngine directive in the .htaccess file in the directory  where WordPress is installed.  I'm sure in apache2.conf would be fine to.  Looks something like this:

<IfModule mod_rewrite.c>
RewriteEgine On
</IfModule>

I found this in /etc/gallery/htaccess.
```
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /gallery/

RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^([^\.\?/]+)/([0-9]+)$      /gallery/view_photo.php?set_albumName=$1&index=$2       [QSA]
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^([^\.\?/]+)/([A-Za-z_0-9\-]+)$     /gallery/view_photo.php?set_albumName=$1&id=$2  [QSA]
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^([^\.\?/]+)/$      /gallery/$1     [R]
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^([^\.\?/]+)$       /gallery/view_album.php?set_albumName=$1
[QSA]
</IfModule>

```

I find no directive for the mod_rewrite in /etc/apache2/apache2.conf. I'm using an Athlon Duron 1.3ghz, 256M ram, 2x10 gig hd's. Running breezy, apache2, gallery1.5 to host a dyndns.org home site.

-mark

---

### Post by Todd_Z on 2005-11-12
```

/etc/init.d/apache2 start
 * Starting web server (Apache2)...                                      [fail]

```

I used the sudo a2enmod rewrite command it enabled it properly, but now apache2 wont start.... any ideas?

---

### Post by jalanbuntu on 2005-12-01
To enable the mod_rewrite module at apache, I just simply do this 3 step:

First, add the rewrite.load to /etc/apache2/mods-enabled/
```
sudo ln -s /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled/
```

Second, edit the apache configuration for my virtualhosting. For example, in my computer I only have one virtual hosting (/var/www) that is default from installation, so I make some adjustment for that (In my case I have to edit this file /etc/apache2/sites-enabled/000-default)
```
sudo vi /etc/apache2/sites-enabled/000-default
```
Change the **Allowoverride** value to **all** for the document root directory
For example, I made change to this part of the configuration:
```
        
       <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride [COLOR="Red"]**all**[/COLOR]
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

```

Finnaly, just restart the apache
```
sudo /etc/init.d/apache2 restart
```

I dont't have any problem when try to install wordpress and get it's mod_rewrite rules works for my local site. Just put the .htaccess ,which has the **RewriteEngine On**, at the wordpress installation directory.

Wish that could help ;)

---

### Post by Vinze on 2007-06-25
> **jalanbuntu said:**
> To enable the mod_rewrite module at apache, I just simply do this 3 step:

First, add the rewrite.load to /etc/apache2/mods-enabled/
```
sudo ln -s /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled/
```

Second, edit the apache configuration for my virtualhosting. For example, in my computer I only have one virtual hosting (/var/www) that is default from installation, so I make some adjustment for that (In my case I have to edit this file /etc/apache2/sites-enabled/000-default)
```
sudo vi /etc/apache2/sites-enabled/000-default
```
Change the **Allowoverride** value to **all** for the document root directory
For example, I made change to this part of the configuration:
```
        
       <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride [COLOR="Red"]**all**[/COLOR]
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

```

Finnaly, just restart the apache
```
sudo /etc/init.d/apache2 restart
```

I dont't have any problem when try to install wordpress and get it's mod_rewrite rules works for my local site. Just put the .htaccess ,which has the **RewriteEngine On**, at the wordpress installation directory.

Wish that could help ;)

It helped me, thanks a lot!

---

### Post by thePFY on 2007-08-20
> **neocon2005 said:**
> Thank you very much for the answer. Worked very well for me. Goes to show that even though the reply was delayed, it can still be useful for people searching for information at a much later date - people like me!!!

i'd like second that

:) :)

---

### Post by falldog7 on 2007-08-24
> **jalanbuntu said:**
> To enable the mod_rewrite module at apache, I just simply do this 3 step:

First, add the rewrite.load to /etc/apache2/mods-enabled/
```
sudo ln -s /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled/
```

Second, edit the apache configuration for my virtualhosting. For example, in my computer I only have one virtual hosting (/var/www) that is default from installation, so I make some adjustment for that (In my case I have to edit this file /etc/apache2/sites-enabled/000-default)
```
sudo vi /etc/apache2/sites-enabled/000-default
```
Change the **Allowoverride** value to **all** for the document root directory
For example, I made change to this part of the configuration:
```
        
       <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride [COLOR="Red"]**all**[/COLOR]
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

```

Finnaly, just restart the apache
```
sudo /etc/init.d/apache2 restart
```

I dont't have any problem when try to install wordpress and get it's mod_rewrite rules works for my local site. Just put the .htaccess ,which has the **RewriteEngine On**, at the wordpress installation directory.

Wish that could help ;)


This method I had try. But it's not work.....:(
I look my apache module list
```
apache2 -l
```
There are not have mod_rewrite.c
Why????

And I try see my web page
<?
  phpinfo
?>
mod_rewrite is in Loaded Modules

What can I do....

---

### Post by werebus on 2007-10-21
> **falldog7 said:**
> 
...
I look my apache module list
```
apache2 -l
```
There are not have mod_rewrite.c
Why????

And I try see my web page
<?
  phpinfo
?>
mod_rewrite is in Loaded Modules
...
```
apache2 -l
``` only shows modules that were included in Apache at compile time (static modules).  If you installed Apache2 using Ubuntu's packages or their installer, mod_rewrite will not be there -- this is a good thing, if a user doesn't need it they don't have to load it.  You should instead try ```
 apache2ctl -t -D DUMP_MODULES
``` to list all currently loaded modules both static and dynamic.

---

### Post by antofthy on 2007-11-07
Thank upi for your help here.

I already has Rewrite Rules in place but in my switch to Ubuntu they stopped working.

Basically I wanted a  ".htaccess" file could appear no a number of machines but I wanted it to redirect users to the correct position on a different server if they attempted to access the directory on one specific server.

That is redirect one specific server to another URL.

This was the solution...

```

<IfModule mod_rewrite.c>
RewriteEngine On
RewriteCond %{SERVER_NAME} ^www\.from\.this\.server
RewriteRule ^(.*)$  http://www.to.tis.server/Usage/$1  [R,L,QSA]
</IfModule>

```
Basically if a user attempts to get say  "this/file" from the directory in which the ".htaccess" file, they will be redirected to  "http://www.to.tis.server/Usage/this/file"  instead.  All very neat, clean and relative to the ".htaccess" file at the top of that directory tree.
:)

---

### Post by tommyvon on 2008-02-21
> **werebus said:**
>   You should instead try ```
 apache2ctl -t -D DUMP_MODULES
``` to list all currently loaded modules both static and dynamic.

This syntax only gives me this:

```


$ apache2 -t -D DUMP_MODULES
Syntax OK


```

any idea why?

---

### Post by dage on 2008-02-28
> **jalanbuntu said:**
> To enable the mod_rewrite module at apache, I just simply do this 3 step:

First, add the rewrite.load to /etc/apache2/mods-enabled/
```
sudo ln -s /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled/
```

Second, edit the apache configuration for my virtualhosting. For example, in my computer I only have one virtual hosting (/var/www) that is default from installation, so I make some adjustment for that (In my case I have to edit this file /etc/apache2/sites-enabled/000-default)
```
sudo vi /etc/apache2/sites-enabled/000-default
```
Change the **Allowoverride** value to **all** for the document root directory
For example, I made change to this part of the configuration:
```
        
       <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride [COLOR="Red"]**all**[/COLOR]
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

```

Finnaly, just restart the apache
```
sudo /etc/init.d/apache2 restart
```

I dont't have any problem when try to install wordpress and get it's mod_rewrite rules works for my local site. Just put the .htaccess ,which has the **RewriteEngine On**, at the wordpress installation directory.

Wish that could help ;)

it rocks, thanks u :)

---

### Post by babajc on 2008-05-04
> **tommyvon said:**
> This syntax only gives me this:

```


$ apache2 -t -D DUMP_MODULES
Syntax OK


```

any idea why?

It would seem you have ZERO modules loaded.

---

### Post by macness on 2008-06-06
Argh this is frustrating me to no end!](*,)

I'm trying to install wordpress on an Ubuntu Server, Apache 2, etc... 

I've looked through tons of documentation and still get problems with changing my permalinks. (404 errors) I been on the wordpress forums looking for answers, apache guides, sigh.. so far here's what I got...

in my /var/www/blog/.htaccess file I have 
```
# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /blog/
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /blog/index.php [L]
</IfModule>

# END WordPress
```

I have the mod_rewrite in the mods enabled folder so ITS THERE and I edited the virtual host to say (changed everything to AllowOverride None to All):

```
DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride All
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride All
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```


and then restarted the apache server. STILL DOESN'T WORK!

Friends, Comrads, My Dear Ubuntu Family - HELP!

---

### Post by andrewski on 2008-06-09
> **macness said:**
> I edited the virtual host to say (changed everything to AllowOverride None to All):

```
DocumentRoot /var/www/
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
```
What if you create a new DocumentRoot/Directory for /var/www/blog? I don't know much, but I'd wonder if that'd make a difference.

---

### Post by macness on 2008-06-09
> **andrewski said:**
> What if you create a new DocumentRoot/Directory for /var/www/blog? I don't know much, but I'd wonder if that'd make a difference.

Are you suggesting something like ??:

```
DocumentRoot /var/www/blog
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /var/www/blog>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
```

That just may be easy enough to work!

---

### Post by andrewski on 2008-06-09
> **macness said:**
> Are you suggesting something like ??:

```
DocumentRoot /var/www/blog
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /var/www/blog>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
```
Right, *in addition* to the one you have for /var/www. If I recall (and it's been a while :oops:) you can have multiple of those. I do think they're recursive—i.e. in this case, setting one for /var/www should be sufficient for the blog subfolder—but it's an easy enough thing to test. :)

---

### Post by macness on 2008-06-10
> **andrewski said:**
> Right, *in addition* to the one you have for /var/www. If I recall (and it's been a while :oops:) you can have multiple of those. I do think they're recursive—i.e. in this case, setting one for /var/www should be sufficient for the blog subfolder—but it's an easy enough thing to test. :)

didn't work :( I'm a bit at a loss, but this isn't the apache or wordpress forums so I may need to heckle a bit over on the WP forums for help too.

---

### Post by sewmyheadon on 2008-06-20
> **jalanbuntu said:**
> To enable the mod_rewrite module at apache, I just simply do this 3 step:

Thanks a bunch!  That worked for me too!

---

### Post by kenne on 2008-06-26
> **jalanbuntu said:**
> To enable the mod_rewrite module at apache, I just simply do this 3 step:

First, add the rewrite.load to /etc/apache2/mods-enabled/
```
sudo ln -s /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled/
```

Second, edit the apache configuration for my virtualhosting. For example, in my computer I only have one virtual hosting (/var/www) that is default from installation, so I make some adjustment for that (In my case I have to edit this file /etc/apache2/sites-enabled/000-default)
```
sudo vi /etc/apache2/sites-enabled/000-default
```
Change the **Allowoverride** value to **all** for the document root directory
For example, I made change to this part of the configuration:
```
        
       <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride [COLOR="Red"]**all**[/COLOR]
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

```

Finnaly, just restart the apache
```
sudo /etc/init.d/apache2 restart
```

I dont't have any problem when try to install wordpress and get it's mod_rewrite rules works for my local site. Just put the .htaccess ,which has the **RewriteEngine On**, at the wordpress installation directory.

Wish that could help ;)

Thanks, that worked perfectly for me!

---

### Post by shahjapan on 2008-07-03
Thanks dude,

it works

```
       <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride all
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
        </Directory>
```

I changed apache2/default file.

---

