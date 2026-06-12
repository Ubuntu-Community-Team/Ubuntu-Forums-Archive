---
title: "cannot test any php files at http://localhost   HELP"
date: 2007-03-06
forum: Server Platforms
---

### Post by ateet101 on 2007-03-06
i used [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) to set everything up
i made a test.php file and put it in /var/www when i put [http://localhost/test.php](http://localhost/test.php)   it will not load the page.  i am sure that apache is running because when i try to start it it says apache is running

---

### Post by Heliix on 2007-03-06
what **exactly** do you see?
first, make sure apache is started with php5 module. see the apache2.conf file and see if the module is loaded at start, or run command apache -l to check if it is built-in.

does it offer only to download the test.php file or view its source?
then check your test.php has permissions for executing, if not, set them with 
$ chmod +x test.php

or is it "page not found" error?
check the location of your test.php, it should be in Apache web root (see /etc/apache2/apache2.conf and set your web root here)

or "access forbidden-permission denied"?
set permissions to your test.php (you may need to run this command as root)
# chmod 755 test.php  

hope it helps!

---

### Post by conjur3r on 2007-03-06
PHP files do not need executable permissions unless PHP was loaded as a CGI module which the guide does not tell you to do.

Always check your apache error logs in /var/log.  This file will tell you if errors were encountered when apache booted up, what happened when you requested the php file, etc...

So what did actually happen?

---

### Post by Heliix on 2007-03-06
> **conjur3r said:**
> PHP files do not need executable permissions unless PHP was loaded as a CGI module which the guide does not tell you to do.

thanks for correction. I always had the CGI module and I didn't realize the difference.

---

### Post by Shantesh on 2007-03-07
i have a similar problem i have installed apache,php,mysql
but my test.php just doesnt seem to work. Apache2 runs properly as i can see apache2-default but my other test.php doesnt work. It just keeps on asking me to download/open with that file when i type in [http://localhost/test.php](http://localhost/test.php)
Please someone help
thanks in advance

---

### Post by Mr. C. on 2007-03-07
Be sure you have the lines:

<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

in your php.conf file.  This is the default configuration if you used synaptec to install.

---

### Post by Shantesh on 2007-03-07
i dont have a php.conf file, i tried adding it in apache.conf in /etc/apache2/, but doesnt work, if the php.conf file does exist where it could be?

---

### Post by Mr. C. on 2007-03-07
Really the question is, from where did you get your apache and php !

This file would have been installed for you if you installed via Synaptec.  If you installed from source, the installer will attempt to add this information to the apache configuration area.

MrC

---

### Post by Shantesh on 2007-03-07
i did it through synaptic, i tried adding the lines in apache2.conf but doesnt work
what do i do?

---

### Post by Mr. C. on 2007-03-07
Don't thrash, adding lines to random places you don't understand.  Work to understand what's going wrong.

Synaptec would add php5.conf and several other files here:

 ls -l /etc/apache2/mods-enabled/  
total 0
lrwxrwxrwx 1 root root 36 Mar  3 12:58 cgi.load -> /etc/apache2/mods-available/cgi.load
lrwxrwxrwx 1 root root 37 Mar  5 23:00 php5.conf -> /etc/apache2/mods-available/php5.conf
lrwxrwxrwx 1 root root 37 Mar  5 23:00 php5.load -> /etc/apache2/mods-available/php5.load
lrwxrwxrwx 1 root root 40 Mar  3 12:58 userdir.conf -> /etc/apache2/mods-available/userdir.conf
lrwxrwxrwx 1 root root 40 Mar  3 12:58 userdir.load -> /etc/apache2/mods-available/userdir.load

Are you saying you don't have any of those?

Go through the troubleshooting section of the guide you followed.

MrC

---

### Post by Shantesh on 2007-03-07
hey found it..
php.conf says

<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>


but still it doesnt work..

---

### Post by scxtt on 2007-03-07
not sure if this'll make a difference, and it's from my gentoo install of apache2 and php5, but ... this is in file "/etc/apache2/modules.d/70_mod_php5.conf" (if yours is setup like that, it might have a different filename):
```
[font=courier]<IfDefine PHP5>

        # Load the module first
        <IfModule !mod_php5.c>
                LoadModule php5_module    modules/libphp5.so
        </IfModule>

        # Set it to handle the files
        <IfModule mod_mime.c>
                AddType application/x-httpd-php .php
                AddType application/x-httpd-php .phtml
                AddType application/x-httpd-php .php3
                AddType application/x-httpd-php .php4
                AddType application/x-httpd-php .php5
                AddType application/x-httpd-php-source .phps
        </IfModule>

        AddDirectoryIndex index.php index.phtml
</IfDefine>[/font]
```just a thought :)

---

### Post by Shantesh on 2007-03-07
tried ..didnt work

still doesnt work !!!

if anyone wants me to put up any conf file or output of any command let me know

---

### Post by Mr. C. on 2007-03-07
The Synaptec version create the file /etc/apache2/mods-enabled/php5.load, which contains the appropriate line.  The OP has missed something in the setup.

# cat /etc/apache2/mods-enabled/php5.load      
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so

Perhaps apache was not restarted?

Look in your /var/log/apache2/error.log and access.log.  Show any errors.

MrC

---

### Post by Shantesh on 2007-03-07
i restart everytime after editing conf file

[PHP][Tue Mar 06 22:37:51 2007] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec2)
[Tue Mar 06 22:37:51 2007] [notice] mod_python: Creating 20 session mutexes based on 20 max processes and 0 max threads.
[Tue Mar 06 22:37:51 2007] [notice] Apache/2.0.55 (Ubuntu) mod_python/3.1.4 Python/2.4.3 mod_ssl/2.0.55 OpenSSL/0.9.8a configured -- resuming normal operations
[Tue Mar 06 22:44:27 2007] [notice] caught SIGTERM, shutting down
[Tue Mar 06 22:44:28 2007] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec2)
[Tue Mar 06 22:44:28 2007] [notice] mod_python: Creating 20 session mutexes based on 20 max processes and 0 max threads.
[Tue Mar 06 22:44:29 2007] [notice] Apache/2.0.55 (Ubuntu) mod_python/3.1.4 Python/2.4.3 mod_ssl/2.0.55 OpenSSL/0.9.8a configured -- resuming normal operations
[Tue Mar 06 23:05:45 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin
[Tue Mar 06 23:05:45 2007] [error] [client 127.0.0.1] unable to include potential exec "include/top.html" in parsed file /usr/share/apache2/error/HTTP_NOT_FOUND.html.var
[Tue Mar 06 23:05:45 2007] [error] [client 127.0.0.1] unable to include potential exec "include/bottom.html" in parsed file /usr/share/apache2/error/HTTP_NOT_FOUND.html.var
[Tue Mar 06 23:33:36 2007] [notice] caught SIGTERM, shutting down
[Tue Mar 06 23:33:37 2007] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec2)
[Tue Mar 06 23:33:37 2007] [notice] mod_python: Creating 20 session mutexes based on 20 max processes and 0 max threads.
[Tue Mar 06 23:33:37 2007] [notice] Apache/2.0.55 (Ubuntu) mod_python/3.1.4 Python/2.4.3 mod_ssl/2.0.55 OpenSSL/0.9.8a configured -- resuming normal operations
[Tue Mar 06 23:36:22 2007] [notice] caught SIGTERM, shutting down
[Tue Mar 06 23:36:24 2007] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec2)
[Tue Mar 06 23:36:24 2007] [notice] mod_python: Creating 20 session mutexes based on 20 max processes and 0 max threads.
[Tue Mar 06 23:36:24 2007] [notice] Apache/2.0.55 (Ubuntu) mod_python/3.1.4 Python/2.4.3 mod_ssl/2.0.55 OpenSSL/0.9.8a configured -- resuming normal operations
[Tue Mar 06 23:49:51 2007] [notice] caught SIGTERM, shutting down
[Tue Mar 06 23:49:53 2007] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec2)
[Tue Mar 06 23:49:53 2007] [notice] mod_python: Creating 20 session mutexes based on 20 max processes and 0 max threads.
[Tue Mar 06 23:49:54 2007] [notice] Apache/2.0.55 (Ubuntu) mod_python/3.1.4 Python/2.4.3 PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a configured -- resuming normal operations[/PHP]

---

### Post by Mr. C. on 2007-03-07
This line tells us PHP is loaded and running:

Tue Mar 06 23:49:54 2007] [notice] Apache/2.0.55 (Ubuntu) mod_python/3.1.4 Python/2.4.3 PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a configured -- resuming normal operations

I see at least one unrelated error:

[Tue Mar 06 23:05:45 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin

What I don't see are any accesses or errors showing you tried test.php.  Search both logs for test.php and show all those lines.

What are the permissions of your test.php file ?

MrC

---

### Post by deejaybes on 2007-03-07
I had the same problem. I installed (and re-installed) apache2 and php5 (and php4) over and over again... Allways the same "save/run with"-problem.

Then i found this : [https://help.ubuntu.com/6.10/ubuntu/serverguide/C/php5.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/php5.html)

and my problems went away! The key wat that for some reason the Synaptic- installation didn't add nessesery files in "/etc/apache2/mods-enabled/"-folder. 

i ran command:
```
sudo a2enmod php5
```
in the folder mentioned before and after restarting Apache2 php worked just fine.

---

### Post by Shantesh on 2007-03-07
looks like there was a missing package..things got sorted out after reinstallation
thanks a lot for your help guys...really appreciate it ! :)

---

### Post by Mr. C. on 2007-03-07
> **Shantesh said:**
> looks like there was a missing package..things got sorted out after reinstallation
thanks a lot for your help guys...really appreciate it ! :)

Good to hear.  Lesson learned... if one blindly follows someone's  instructions, be prepared to walk into walls.

MrC

---

### Post by pppetter on 2007-03-08
Just a little tip for the future Shantesh, you can Copy & Paste the commands that you find in guides or here on the forum, this way you won't make a typo (or forget a package...).

---

