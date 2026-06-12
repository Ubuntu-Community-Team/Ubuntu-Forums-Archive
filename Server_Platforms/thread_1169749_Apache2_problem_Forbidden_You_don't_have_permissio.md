---
title: "Apache2 problem: Forbidden You don't have permission..."
date: 2009-05-25
forum: Server Platforms
---

### Post by afbase on 2009-05-25
Okay,  I am in the last throws of transferring data from my antique server to my old server.  The trouble is what I believe to be an simple apache2 issue that I can't figure out.

I can't get my darn apache2 to stop forbidding access to my folder.  here is my /etc/apache2/sites-available:
```

NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /home/clinton/online/coldowl/
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
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

<VirtualHost *>
ServerName www.coldowl.com
ServerAlias coldowl.com
DocumentRoot /home/clinton/online/coldowl/
<Directory /home/clinton/online/coldowl>
AllowOverride All
Options ExecCGI Includes
Order allow,deny
Allow from all
</Directory>
</VirtualHost>

```

I have no idea why its not working and i'm not sure this is where I should be looking to resolve the problem.

I've looked on the [apache website]("http://httpd.apache.org/docs/1.3/misc/FAQ.html#forbidden").  It had this to say about the issue:
> 
        **Why do I get a         "Forbidden" message whenever I try to access a         particular directory?**           This message is generally caused because either
          
[LIST]
[*]The underlying file system permissions do not allow           the User/Group under which Apache is running to access           the necessary files; or
[*]The Apache configuration has some access restrictions           in place which forbid access to the files.
[/LIST]
          You can determine which case applies to your situation         by checking the error log.
          In the case where file system permission are at fault,         remember that not only must the directory and files in         question be readable, but also all parent directories must         be at least searchable (i.e., *chmod +x /directory/path*)         by the web server in order for the content to be accessible.

If one looks at the [url=http://httpd.apache.org/docs/1.3/misc/FAQ.html#forbidden] apache website[\url], question 15 says to look for a particular string in that one file.  But there isn't anything in my httpd.conf file.  There is something that looks like it in my apache2.conf

Any help is appreciated.

---

### Post by albinootje on 2009-05-25
> **afbase said:**
> 
DocumentRoot /home/clinton/online/coldowl/
<Directory /home/clinton/online/coldowl>
I've just tried the same but with "localhost" and "/tmp" (just for testing locally), and I got this error in the apache log files :
> 
[Mon May 25 21:15:45 2009] [error] [client 127.0.0.1] Directory index forbidden by Options directive: /tmp/

Then I created an empty index.html in /tmp and.. it worked :)
Do you have an index.html file in that DocumentRoot ?

---

### Post by afbase on 2009-05-25
> **albinootje said:**
> I've just tried the same but with "localhost" and "/tmp" (just for testing locally), and I got this error in the apache log files :

Then I created an empty index.html in /tmp and.. it worked :)
Do you have an index.html file in that DocumentRoot ?

I have an index.php

Not an index.html

Its a drupal installation (i've already pre-tested the drupal locally and it works perfectly. Now I'm trying to make it accessible to the web).  

This is my /etc/apache2/mods-available/dir.conf 
```

<IfModule mod_dir.c>

         #DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
         DirectoryIndex index.html index.htm index.shtml index.cgi index.php index.php3 index.pl index.xhtml



</IfModule>


```I figure that this should imply that apache should read my index.php just fine.

my /etc/mime.types  snippet is as follows:
```

......other stuff......
application/x-hdf                               hdf
application/x-httpd-php                         phtml pht php
application/x-httpd-php-source                  phps
application/x-httpd-php3                        php3
application/x-httpd-php3-preprocessed           php3p
application/x-httpd-php4                        php4
......other stuff......

```you can try accessing the website i'm try to make available at [http://www.coldowl.com](http://www.coldowl.com)

---

### Post by albinootje on 2009-05-25
> **afbase said:**
> I have an index.php

Not an index.html
Please test with an index.html too, and check the permissions of related files and directories.

And.. most important : check your apache log files!

---

### Post by albinootje on 2009-05-25
And did it work as "localhost" before ?

---

### Post by afbase on 2009-05-25
it worked as [http://10.0.0.106/drupal/](http://10.0.0.106/drupal/)

The folder was in /var/www/drupal/ when i tested it. It have since moved and renamed the folder to /home/clinton/online/coldowl

I just tried restarting apache 2  I got an warning message:
```

[Mon May 25 12:55:04 2009] [warn] NameVirtualHost *:80 has no VirtualHosts

```
any reason for this?

---

### Post by afbase on 2009-05-25
> **albinootje said:**
> Please test with an index.html too, and check the permissions of related files and directories.

And.. most important : check your apache log files!
I'll try just that as soon as i can.

---

### Post by afbase on 2009-05-25
well here is a snippet of the most recent errors in my error log (/var/log/apache2/error.log) :

```

[Mon May 25 12:59:16 2009] [crit] [client 65.55.106.158] (13)Permission denied: /home/clinton/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
[Mon May 25 12:59:59 2009] [crit] [client 66.249.68.169] (13)Permission denied: /home/clinton/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
[Mon May 25 13:00:13 2009] [crit] [client 38.99.13.119] (13)Permission denied: /home/clinton/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
[Mon May 25 13:00:21 2009] [crit] [client 10.0.0.1] (13)Permission denied: /home/clinton/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable, referer: http://ubuntuforums.org/showthread.php?p=7344759


```

I think the problem is observable to me.  But it is not something I know how to fix.

---

### Post by afbase on 2009-05-25
I just looked at my antique server.  There isn't an /home/clinton/.htaccess file there.  So why is it that apache2 is looking for an .htaccess on this server?  should i try:
```

~$ touch .htaccess

```
?

---

### Post by afbase on 2009-05-25
BUMP
---------------and Side Note---------------------
Ok which one of you decided to send me a message by telling my to encrypt my home directory?
```

clinton@coldowl:/etc/apache2/sites-available$ sudo vim default
clinton@coldowl:/etc/apache2/sites-available$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                                                 Warning: DocumentRoot [/home/clinton/online/coldowl/] does not exist
Warning: DocumentRoot [/var/www/phpmyadmin] does not exist
Warning: DocumentRoot [/home/clinton/online/gallery2/] does not exist
Warning: DocumentRoot [/home/clinton/online/torrentflux/html] does not exist
Warning: DocumentRoot [/home/clinton/online/phpBB3] does not exist
Warning: DocumentRoot [/home/clinton/online/cmb] does not exist
Warning: DocumentRoot [/home/clinton/online/magnumjones] does not exist
Warning: DocumentRoot [/home/clinton/online/torrentbart/html] does not exist
[Mon May 25 19:26:09 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting Warning: DocumentRoot [/home/clinton/online/coldowl/] does not exist
Warning: DocumentRoot [/var/www/phpmyadmin] does not exist
Warning: DocumentRoot [/home/clinton/online/gallery2/] does not exist
Warning: DocumentRoot [/home/clinton/online/torrentflux/html] does not exist
Warning: DocumentRoot [/home/clinton/online/phpBB3] does not exist
Warning: DocumentRoot [/home/clinton/online/cmb] does not exist
Warning: DocumentRoot [/home/clinton/online/magnumjones] does not exist
Warning: DocumentRoot [/home/clinton/online/torrentbart/html] does not exist
[Mon May 25 19:26:10 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                                                                                                                          [ OK ]
clinton@coldowl:/etc/apache2/sites-available$ cd ~
clinton@coldowl:~$ cd online
-bash: cd: online: No such file or directory
clinton@coldowl:~$ ls
Access-Your-Private-Data.desktop  README.txt
clinton@coldowl:~$ vim README.txt 
clinton@coldowl:~$ ecryptfs-mount-private
clinton@coldowl:~$ ls
Access-Your-Private-Data.desktop  README.txt

```I'm not mad, just a bit wierded out by it all.  I've been hacked before and its no fun.  I guess this is more of a thank you than anything else.
---------------------------
all my files are back  though.  Same problem though.  

I found someone having a similar/same problem but on httpd ([link]("http://www.phpfreaks.com/forums/index.php?topic=243271.0")).  He found a solution however I don't believe that would work for apache2.  maybe this link could help you guys revise a solution because chcon  commands are above my head.

---

### Post by albinootje on 2009-05-25
> **afbase said:**
> 
I found someone having a similar/same problem but on httpd ([link]("http://www.phpfreaks.com/forums/index.php?topic=243271.0")).  

Be very careful with chmod commands like that, esp. the "chmod 777" suggestions.

Why don't you want your website in /var/www actually ?
Is it because you want to be able to easily work on your files ?

And you're saying that your webserver got broken into ?
Are you sure ? You can check the apache log files to see what happened.

---

### Post by afbase on 2009-05-26
> **albinootje said:**
> Be very careful with chmod commands like that, esp. the "chmod 777" suggestions.

Why don't you want your website in /var/www actually ?
Is it because you want to be able to easily work on your files ?

And you're saying that your webserver got broken into ?
Are you sure ? You can check the apache log files to see what happened.


** Why don't you want your website in /var/www actually ?**
*Is it because you want to be able to easily work on your files ?*
Thats how I had it before, but I suppose it wouldn't be a problem to do that. I just found it easier that way when I transferred all my data from my antique server to this newer one.  

[B]
And you're saying that your webserver got broken into ?
[/B]
Well how else could it explain when i restarted my apache2 that none of the folders existed?  
```

sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                                                 Warning: DocumentRoot [/home/clinton/online/coldowl/] does not exist
Warning: DocumentRoot [/var/www/phpmyadmin] does not exist
Warning: DocumentRoot [/home/clinton/online/gallery2/] does not exist
Warning: DocumentRoot [/home/clinton/online/torrentflux/html] does not exist
Warning: DocumentRoot [/home/clinton/online/phpBB3] does not exist
Warning: DocumentRoot [/home/clinton/online/cmb] does not exist
Warning: DocumentRoot [/home/clinton/online/magnumjones] does not exist
Warning: DocumentRoot [/home/clinton/online/torrentbart/html] does not exist

```
I then went to my home folder and found nothing was there but a readme.txt and a desktop icon.  The icon would have had me encrypt my directory and the readme file told me to execute the same code.  I know for sure that I didn't do that.  

[B]Are you sure ?
[/B]I'm not sure what apache log to verify this.  But it seems very wierd that my files in my home folder were there in the morning and then when I get home, I find them gone but two files telling me to encrypt the home folder.


I suppose I'll try moving everything to my /var/www/ by symbolic links.  I'll let you know how that goes.

---

### Post by afbase on 2009-05-26
> **afbase said:**
> ** Why don't you want your website in /var/www actually ?**
*Is it because you want to be able to easily work on your files ?*
Thats how I had it before, but I suppose it wouldn't be a problem to do that. I just found it easier that way when I transferred all my data from my antique server to this newer one.  

[B]
And you're saying that your webserver got broken into ?
[/B]
Well how else could it explain when i restarted my apache2 that none of the folders existed?  
```

sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                                                 Warning: DocumentRoot [/home/clinton/online/coldowl/] does not exist
Warning: DocumentRoot [/var/www/phpmyadmin] does not exist
Warning: DocumentRoot [/home/clinton/online/gallery2/] does not exist
Warning: DocumentRoot [/home/clinton/online/torrentflux/html] does not exist
Warning: DocumentRoot [/home/clinton/online/phpBB3] does not exist
Warning: DocumentRoot [/home/clinton/online/cmb] does not exist
Warning: DocumentRoot [/home/clinton/online/magnumjones] does not exist
Warning: DocumentRoot [/home/clinton/online/torrentbart/html] does not exist

```I then went to my home folder and found nothing was there but a readme.txt and a desktop icon.  The icon would have had me encrypt my directory and the readme file told me to execute the same code.  I know for sure that I didn't do that.  

[B]Are you sure ?
[/B]I'm not sure what apache log to verify this.  But it seems very wierd that my files in my home folder were there in the morning and then when I get home, I find them gone but two files telling me to encrypt the home folder.


I suppose I'll try moving everything to my /var/www/ by symbolic links.  I'll let you know how that goes.


I can confirm that my system was comprimised.  I've found folders and files that are not mine on the server.   

What logs can I check to see when I was comprimised?

---

### Post by albinootje on 2009-05-26
> **afbase said:**
>  What logs can I check to see when I was comprimised?

Look in /var/log/apache2/

---

### Post by albinootje on 2009-05-26
> **afbase said:**
> 
I suppose I'll try moving everything to my /var/www/ by symbolic links.

I think it makes more sense to move everything in /var/www and then have a symbolic in your home directory pointing to that. You might also want to try the chroot module for apache, and improve security of apache itself.

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=apache+chroot](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=apache+chroot)

[http://httpd.apache.org/docs/2.0/misc/security_tips.html](http://httpd.apache.org/docs/2.0/misc/security_tips.html)

[http://www.securityfocus.com/infocus/1786](http://www.securityfocus.com/infocus/1786)
[http://ubuntuforums.org/showthread.php?t=1008475](http://ubuntuforums.org/showthread.php?t=1008475)
[http://www.securityfocus.com/infocus/1786](http://www.securityfocus.com/infocus/1786)
[http://www.debuntu.org/2006/08/13/86-secure-your-apache2-with-mod-security](http://www.debuntu.org/2006/08/13/86-secure-your-apache2-with-mod-security)

---

