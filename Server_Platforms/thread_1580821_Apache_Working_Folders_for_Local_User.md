---
title: "Apache: Working Folders for Local User"
date: 2010-09-23
forum: Server Platforms
---

### Post by Nazaroo on 2010-09-23
I want to setup a folder (several really) for websites that use PHP. 

I am running Linux Ubuntu with PHP, APACHE installed.

The Apache server works in Firefox as 127.0.1.1 no problem.

The default directory is (DocumentRoot) /var/www  
This is stored in a file called /etc/apache2/sites-enabled/000-default

PHP executes no problem, if it is in the default directory (/var/www).

However, I'd like to activate PHP in a folder on another hard-drive (also).

In that folder I'd like to store several websites, all which will use PHP and MYSQL.

The problem is, my boot drive where /var/www currently is located has only 2 gig of space (21 gig for operating system, which seems high).  

PHP files in the other hard drive do not execute, even under APACHE server.

How can I safely change the PHP enabled folder?
How can I add more folders, without erasing the current one?

thanks
Nazaroo

---

### Post by koenn on 2010-09-25
you can point apache to any directory you want, it doen't need to be /var/www. 
you can also use the 'virtual hosts' approach to have multiple websites, each in their own directory.

If your going to do a lot of server-side scripts, you might also want to look into the 'SriptAlias' directive.

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html)


for additional space, you could also just mount a separate drive to /var/www (move the current stuff out of it first)


and 21GB for just an OS is rather a lot, I've seen servers run with only 800 MB  disk space used. You might want to check what's happening there.

---

### Post by SeijiSensei on 2010-09-25
A quick and easy solution might be the Alias directive.  

Suppose you've got a folder called /media/mydisk/myfolder that you want to make available via apache as [http://www.example.com/myfolder](http://www.example.com/myfolder).  In sites-enabled/000-default add the line

Alias     /myfolder    /media/mydisk/myfolder 

under the DocumentRoot directive.  You may also need a <Directory> stanza for that directory as well if you need to override the default configuration that appears as "<Directory />".  If so, create a stanza for /myfolder like this:

<Directory /media/mydisk/myfolder>
   Options Indexes FollowSymLinks MultiViews
</Directory>

and place it below the stanza for <Directory /var/www>.

Also the www-data user needs to be able to read /media/mydisk/myfolder so you'll need to check that it has the appropriate file and directory permissions. 

sudo chmod ugo+r -R /media/mydisk/myfolder

will make the files in myfolder and any subfolders below it world-readable.  If you discover you cannot list the files in a folder, set the "execute" bit on the directory like this:

sudo chmod ugo+rx /media/mydisk/myfolder

and repeat for any subfolders of myfolder.

You'll need to restart apache to activate these changes.

---

