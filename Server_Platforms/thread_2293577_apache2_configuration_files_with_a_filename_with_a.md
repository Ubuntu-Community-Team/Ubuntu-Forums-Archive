---
title: "apache2 configuration files with a filename with a new TLD (with a vhost)"
date: 2015-09-05
forum: Server Platforms
---

### Post by Drone4four on 2015-09-05
I recently just set up a vhosts and assigned it a new DN with a funky new TLD.  It sort of works.  

Here are the contents of my sites-available directory:

```

user@remotehost:/etc/apache2/sites-available$ ls -ls *.conf
4 -rw-r--r-- 1 root root  946 Sep  1  2014 000-default.conf
4 -rw-r--r-- 1 root root 1120 Mar  6  2015 DN1.info.conf
8 -rw-r--r-- 1 root root 6437 Jan  7  2014 default-ssl.conf
4 -rw-r--r-- 1 root root 1173 Sep  1 17:20 DN2.coffee.conf
user@remotehost:/etc/apache2/sites-available$

```

Then I issue:

```

user@remotehost:~$ sudo service apache2 restart

```

I get this:

```
 
* Restarting web server apache2                                         [**fail**] 
 * The apache2 configtest failed.
Output of config test was:
apache2: Syntax error on line 219 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/DN2.conf: No such file or directory
Action 'configtest' failed.
The Apache error log may have more information.
user@remotehost:~$ 

```

Lines 218 and 219 of that configuration file read:

```

218 # Include the virtual host configurations:
219 IncludeOptional sites-enabled/*.conf

```

The apache configtest is looking for DN2.conf and its stopping at DN2.coffee because DN2 ends in .coffee before it reaches .conf.
If I remove the instance of .coffee in my apache2 configuration file name and just call the file, DN2.conf, apache configtest returns this output:

```

user@remotehost:~$ sudo service apache2 restart
 * Restarting web server apache2                                                                                            AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1. Set the 'ServerName' directive globally to suppress this message
                     [ **OK** ]
user@remotehost:~$ 

```

So even the apache2 configuration files named DN1.info.conf and the other DN2.conf (w/o the TLD in the filename), my site works.  But this doesn't feel right.  What am I doing wrong here, folks?

Thanks for your attention.

---

### Post by volkswagner on 2015-09-06
I'm confused. You say:


> **Drone4four said:**
> 

So even the apache2 configuration files named DN1.info.conf and the other DN2.conf (w/o the TLD in the filename), my site works.  But this doesn't feel right.  What am I doing wrong here, folks?

Thanks for your attention.

You say "other" DN2.conf. Should we be seeing DN2.conf and DN2.coffee.conf in your sites-enabled directory?

Please compare sites-enabled and sites-available.

My guess; one of the links is missing for DN2.cofee.conf, or you have a link in sites enabled that points to a file that doesn't exist.


EDIT: you should have no problems with TLD combined with sub domains.

---

### Post by Drone4four on 2015-09-06
> **volkswagner said:**
> 
I'm confused. You say:

> 
So even the apache2 configuration files named DN1.info.conf and the other DN2.conf (w/o the TLD in the filename), my site works. But this doesn't feel right. What am I doing wrong here, folks?
 

You say "other" DN2.conf. Should we be seeing DN2.conf and DN2.coffee.conf in your sites-enabled directory?


Here is what I was trying to convey:
The apache2 configuration files present are named DN1.info.conf and DN2.conf (w/o the .coffee TLD in the filename).  These two files are named as such and are present in both the sites-enabled and sites-available directory.  I just checked and the contents of both those files are identical.  

> 
My guess; one of the links is missing for DN2.cofee.conf, or you have a link in sites enabled that points to a file that doesn't exist.


Here are the contents of these two identical configuration files (with the real sub domain name replaced with 'DN2'):
```

# domain: DN2.coffee
# public: /home/user/public/DN2.coffee

#<VirtualHost *:80>
  # Admin email, Server Name (domain name), and any aliases
#  ServerAdmin webmaster@DN2.coffee
#  ServerName  www.DN2.coffee
#  ServerAlias DN2.coffee

  # Index file and Document Root (where the public files are located)
#  DirectoryIndex index.html
#  DocumentRoot /home/user/public/DN2.coffee/public

  # Log file locations
#  LogLevel warn
#  ErrorLog  /home/user/public/DN2.coffee/log/error.log
#  CustomLog /home/user/public/DN2.coffee/log/access.log combined
# </VirtualHost>

<VirtualHost *:80>

        ServerAdmin webmaster@DN2.coffee
        ServerName  www.DN2.coffee
        ServerAlias DN2.coffee
        DocumentRoot /var/www/html/DN2.coffee/public_html/
        ErrorLog /var/www/html/DN2.coffee/logs/error.log
        CustomLog /var/www/html/DN2.coffee/logs/access.log combined

     <Directory /var/www/html/DN2.coffee/public_html/>
        Order allow,deny
        Allow from all
     </Directory>

</VirtualHost>
```

---

### Post by volkswagner on 2015-09-06
I'm trying to determine if there is a mismatch between directories. The content of the .conf files are not really relevant.

Please post output of the following commands.

```
ls -l /etc/apache2/sites-available
```
and
```
ls -l /etc/apache2/sites-enabled
```

---

### Post by Drone4four on 2015-09-06
```
user@remotehost:/etc/apache2/sites-enabled$ ls -l
total 0
lrwxrwxrwx 1 root root 41 Mar  6  2015 DN1.info.conf -> ../sites-available/DN1.info.conf
lrwxrwxrwx 1 root root 38 Sep  1 17:24 DN2.conf -> ../sites-available/DN2.conf
user@remotehost:/etc/apache2/sites-enabled$
```


```
user@remotehost:/etc/apache2/sites-available$ ls -l
total 20
-rw-r--r-- 1 root root  946 Sep  1  2014 000-default.conf
-rw-r--r-- 1 root root 1120 Mar  6  2015 DN1.info.conf
-rw-r--r-- 1 root root 6437 Jan  7  2014 default-ssl.conf
-rw-r--r-- 1 root root 1173 Sep  1 17:20 DN2.conf
user@remotehost:/etc/apache2/sites-available$
```

edit: I btw tried renaming both DN2.confs to DN2.coffee.conf.  The apache2 configtest came back with the error msg I reported earlier.

edit: i changed the file names back to DN2.conf and it passes the apache2 configtest

---

### Post by volkswagner on 2015-09-06
I'm sorry, but I don't know if the commands a2ensite and a2dissite perform other functions other than creating/deleting symlinks in sites-enabled.

For what ever site you are getting error on:"
```
Could not open configuration file /etc/apache2/sites-enabled/DN2.conf
```

I would run:
```
sudo a2dissite DN2
```

Then restart Apache2.

What happens?

What happens when you have just:

```
user@remotehost:/etc/apache2/sites-available$ ls -l
total 20
-rw-r--r-- 1 root root  946 Sep  1  2014 000-default.conf
-rw-r--r-- 1 root root 1120 Mar  6  2015 DN1.info.conf
-rw-r--r-- 1 root root 6437 Jan  7  2014 default-ssl.conf
-rw-r--r-- 1 root root 1173 Sep  1 17:20 DN2.conf
user@remotehost:/etc/apache2/sites-available$
```

Then run 
```
sudo a2ensite DN2
```

Then add third file "/etc/apache2/sites-available/DN2.coffee.conf

Then run:
```
sudo a2ensite DN2.coffee
```

Restart Apache2... what happens?

If you're still having trouble, get a clean slate, disable all sites, name config files as you like in sites-available, then enable each, then start Apache2.

```

sudo su
a2dissite *
service apache2 stop
rm /etc/apache2/sites-enabled/*
a2ensite DN1.info DN2.coffee DN2
service apache2 start

```

---

### Post by Drone4four on 2015-09-07
**@volkswagner **: I regret to say that I have other business which I have to take care of for now.  I will be back in a few days with a decent reply.  Thanks for your help so far, my friend.

---

### Post by Drone4four on 2015-10-13
> **volkswagner said:**
> 
If you're still having trouble, get a clean slate, disable all sites, name config files as you like in sites-available, then enable each, then start Apache2.

```

sudo su
a2dissite *
service apache2 stop
rm /etc/apache2/sites-enabled/*
a2ensite DN1.info DN2.coffee DN2
service apache2 start

```



Between the my last post and today I configured something somehow which renders my 2 virtual hosts and web addresses fully functional and working as intended.  

The contents of /etc/apache2/sites-available remain as follows:
```

$ ls -l
total 20
-rw-r--r-- 1 root root  946 Sep  1  2014 000-default.conf
-rw-r--r-- 1 root root 1120 Mar  6  2015 DN1.info.conf
-rw-r--r-- 1 root root 6437 Jan  7  2014 default-ssl.conf
-rw-r--r-- 1 root root 1324 Oct 13 19:50 DN2.conf
$ 

```
Notice the TLD present for the DN1 file and not the DN2 file.  

It's been a rather long time since my last post. I apologize for my delayed reply. :D

---

