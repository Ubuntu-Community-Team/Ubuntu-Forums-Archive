---
title: "Apache2 and Mod_rewrite problems"
date: 2007-04-23
forum: Server Platforms
---

### Post by xenoix on 2007-04-23
Hey, I just reinstalled kubuntu 6.10 edgy. I have installed PHP5, Apache2 and MySQL 5.

I have now tried enabling mod_rewrite. I have done the following:

root@foobar:/etc/apache2/sites-enabled# a2enmod rewrite
This module is already enabled!

As you can see, i have already enabled mod_rewrite.

I have then done the following:

root@foobar:/etc/apache2/sites-enabled# nano 000-default
(have used vi too)

   DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks
                AllowOverride All
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

As what the tutorial I read said to do. I have done what its asked.

And finally done:
root@foobar:/etc/apache2/sites-enabled# /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...
 apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

                                                                         [ ok ]
root@foobar:/etc/apache2/sites-enabled#      

Its all enabled and restarted etc. However, my problem is. I refresh my webserver and im getting nothing but Forbidden as such:

Forbidden
You don't have permission to access /test on this server.
Apache/2.0.55 (Ubuntu) PHP/5.1.6 Server at 127.0.0.1 Port 80

Forbidden
You don't have permission to access / on this server.
Apache/2.0.55 (Ubuntu) PHP/5.1.6 Server at 127.0.0.1 Port 80

WHY?!?!?!?! I have purged and reinstalled apache2 3 times now. Im getting frustrated and i need to have this going for work.

Any help would be greatly appreciated on resolving this issue.

---

### Post by MilesZS on 2007-04-23
You have a permissions issue, it appears.  You need to run the command 'chmod' on the directories and files that you want the server to be able to access.  If I remember correctly, the recommended commands would be...
```

sudo chmod 755 some_directory/

```
... for a directory, and ...
```

sudo chmod 644 some_file

```
... for a file, such as 'index.php', or 'index.html'.

I hope that helps.

---

### Post by xenoix on 2007-04-23
I dont believe its a permission issue because with out changing that AllowOverride to All the webserver works. However once it has been changed and restarted the server it doesnt work.

And also, since / is an open directory, it shouldnt be forbidden. Netherless i did what you asked and still didnt fix it.

```

scarvell@foobar:/var$ ls -l | grep www
drwxrwxrwx  4 root root  4096 2007-04-23 22:28 www

```

```

root@foobar:/var/www# ls -l
total 16
drwxrwxrwx  2 root     root     4096 2007-04-23 22:28 apache2-default
drwxrwxrwx 10 root     root     4096 2007-04-23 23:51 rat
-rwxrwxrwx  1 root     root        5 2007-04-23 20:25 test.html
-rwxrwxrwx  1 scarvell scarvell    5 2007-04-23 17:34 test.txt

```

The correct permissions are applied :/

---

### Post by Daniel0 on 2007-06-04
nevermind... delete it

---

