---
title: "apache2: bad user name ${APACHE_RUN_USER}"
date: 2008-05-23
forum: Server Platforms
---

### Post by jeroenisblij on 2008-05-23
I am having this problem both on Ubuntu server 8.04 with LAMP, and ubuntu destkop 8.04 with Apache2. I am not having the problem with Debian4 on the same PC.

I just installed a fresh copy of ubuntu server 8.04 on my pc, with LAMP and Samba enabled. Now it seems to work, but whenever i try to restart apache i get this error:```
jeroen@jeroen-desktop:/etc/apache2$ apache2 -k restart
apache2: bad user name ${APACHE_RUN_USER}
```.
The APACHE_RUN_USER var correctly refers to www-data in my /envvars file (i didnt touch that file or anything).
If you google this error, you get the advice to replace the 'User' and 'Group' variable in the config file by:
User www-data
Group www-data

However, when i do this, i get these errors:
```

jeroen@jeroen-desktop:/etc/apache2$ apache2 -k restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
```
There are probably also ways to fix that, but why doesnt it work out of the box, like it should? What did i do wrong? Is there an easy way to fix this?

---

### Post by Rinzwind on 2008-05-23
The cause of the problem is that user and group are pulled from environment.

# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

To fix this problem, You can statically define user and group in your apache.conf

User www-data
Group www-data

---

### Post by jeroenisblij on 2008-05-23
i tried to explain in my post that i get other errors when i do that. Why are user and group not on my environment? How can i add them?

---

### Post by jkobbe on 2008-05-24
I believe this is caused by tryint to run apache with the wrong command.
try "sudo /etc/init.d/apache2 restart" or start, or whatever you are trying to do. This should read in the environment variables correctly with the "out of the box" installation.

---

### Post by AllanJP on 2008-06-08
Hey that helped, I wonder why that helped, and not when I: cd /etc/init.d/ and then typed: apache2 restart ?,

---

### Post by ryanisablond on 2008-06-09
> **AllanJP said:**
> Hey that helped, I wonder why that helped, and not when I: cd /etc/init.d/ and then typed: apache2 restart ?,

AllanJP, the difference is the *sudo*. Apache2 needs to be restarted by the superuser, not just a normal account. That's the only difference between what you were doing and what jkobbe suggested. 

For whatever reason, the command doesn't return the normal "Permission denied" message. Weird, huh?

---

### Post by jkobbe on 2008-06-16
I believe this is because etc/init.d is not in your command path. Unlike Windows, Linux does not look in the "current" directory for commands. So, if you are in /etc/init.d you can type "sudo ./apache2 restart" which will tell it to look in the current directory with the "./" The script in /etc/init.d/apache2 explicitly reads in the environment variables before calling /usr/sbin/apache2. /usr/sbin/ is in yoour command path, so that is the one that runs when you just type "apache2 ..."

---

### Post by adredz on 2008-06-27
hi i have a problem similar to the OP. but mine is:

when i restart apache i get this:

> apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98 )Address already in use: make_sock: could not bind to address 0.0.0.0:443
no listening sockets available, shutting down
Unable to open logs
i think this has something to do with my server name, right? should i change it?how?
i'm sorry this is my first time setting up a server..

---

### Post by bluegene on 2008-06-27
ISPConfig-2.2.23.tar.gz solves the problem in Ubuntu 8.04 LTS

$ wget -c [http://nchc.dl.sourceforge.net/sourceforge/ispconfig/ISPConfig-2.2.23.tar.gz](http://nchc.dl.sourceforge.net/sourceforge/ispconfig/ISPConfig-2.2.23.tar.gz)

---

### Post by Requiem on 2008-07-25
> **jkobbe said:**
> I believe this is caused by tryint to run apache with the wrong command.
try "sudo /etc/init.d/apache2 restart" or start, or whatever you are trying to do. This should read in the environment variables correctly with the "out of the box" installation.

Thank you, these fixed my problem

---

### Post by edcard on 2008-08-08
"...try "sudo /etc/init.d/apache2 restart"..."

Thanks! I had the same problem, but everything's OK now. I agree that values should be read from envvars.

---

### Post by Fjan on 2008-11-01
You may still need to run sudo apache2 directly if you need certain command line options, for example you need "sudo apache -t" to check the syntax of a conf that references SSL certificates.

In that case just prefix the command with the variables like this:
sudo APACHE_RUN_USER=www-data APACHE_RUN_GROUP=www-data apache2 -t

---

### Post by instabil on 2008-11-13
/etc/init.d/apache2 is great if you want to do any of the following:

[LIST]
[*]start
[*]stop
[*]restart
[*]reload
[*]force-reload
[*]start-htcacheclean
[*]stop-htcacheclean
[*]status
[/LIST]

But if you need to run apache2 with arguments (for example "apache2 -S" for checking your virtualhost settings) you *could* prefix the command like Fjan suggested above but I think it's easier to use the apache2ctl command like this:

# apache2ctl -S

---

### Post by Fjan on 2008-11-13
> apache2ctl -S
You are right, that is much more convenient than setting the environment vars by hand. Thanks.

---

### Post by crouz on 2009-01-25
> **adredz said:**
> hi i have a problem similar to the OP. but mine is:

when i restart apache i get this:


i think this has something to do with my server name, right? should i change it?how?
i'm sorry this is my first time setting up a server..

You need to define your ServerName in /etc/apache2/apache2.conf, e.g

[FONT="Courier New"]
ServerName "www.myDomain.com"
[/FONT]

---

### Post by moanin on 2009-02-06
ServerName "www.myDomain.com"

or

ServerName localhost

worked fine for me.

thank to all

---

### Post by matey3 on 2009-03-16
Also just for the record and in case some one else has the same problem as I did with ${APACHE_RUN_USER} error:

I installed Plone and then it required for me to have sec. certs.
I could not run apache2 -k start no matter what. So I went in the /etc/apache2/sites-enabled and removed that plone.conf (Or any other conf file that generates the error) Remember renaming the conf file in that directory will Not help as long as it's in there it will be read.

I moved the bad.conf file to my home directory and apache started to run again?!

The running of apache from /etc/init.d plus --force-reload switched helped me to figure out which file was responsible.
So thanks to all who helped.

---

### Post by pgn674 on 2009-03-26
> **AllanJP said:**
> Hey that helped, I wonder why that helped, and not when I: cd /etc/init.d/ and then typed: apache2 restart ?,Probably because you should have done "./apache2 restart" instead of "apache2 restart", as well as sudo as others have pointed out. Without the "./", the computer uses the environment variables to look for an executable by that name. If you use "./", the directory you are currently browsing is used to look for that executable.

---

### Post by wesamly on 2009-11-07
I was trying to figure if mod_rewrite is loaded, when I run:
```
sudo apache2 -M
```I get the same error:
[COLOR=Red]apache2: bad user name ${APACHE_RUN_USER}[/COLOR]
tried restarting apache:
```
sudo /etc/init.d/apache2 restart
```but still the same, but using:
```
apache2ctl -M
```I got it to work!
I'll check later for solution, thought it may help someone.

---

### Post by jmjegou on 2010-07-22
hello ,

when i  connect to htt://localhost/ or [http://127.0.0.1/](http://127.0.0.1/) (with original config file) ,it doesn't works !
because  "bad user name ${APACHE_RUN_USER}" ,you know that !

After :

[LIST]
[*]apache2 restart
[*]and try [http://127.0.1.1/](http://127.0.1.1/) , it works !
[/LIST]

;)

---

### Post by *_K16_* on 2010-11-02
"sudo /etc/init.d/apache2 restart"

Thanks worked right away. :D

---

### Post by r00t4rd3d on 2010-12-16
sudo apache2ctl restart
sudo apache2ctl stop
sudo apache2ctl start

:D

---

### Post by slavelabor on 2012-10-06
```

jeroen@jeroen-desktop:/etc/apache2$ apache2 -k restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
```

I have corrected the FQDN error by adding 
```

# httpd.conf
ServerName my_servername
```

Also, Apache starts as root and changes to the defined apache user; apachectl needs to be executed as root. If you shell into a remote server as root, you don't need sudo. On your local machine, you probably aren't root and need sudo or su.

---

### Post by lisati on 2012-10-06
What happens when you try this?
```
sudo servive apache2 restart
```

---

### Post by mightypile on 2013-07-12
> **AllanJP said:**
> Hey that helped, I wonder why that helped, and not when I: cd /etc/init.d/ and then typed: apache2 restart ?,

Your shell will run the first executable apache2 file it finds. If you path has in it, in this order, "/usr/local/sbin:." the apache2 executable will be run from /usr/local/sbin/apache2 no matter where you've cd'ed to. If, however, your path has in it, in this order, ".:/usr/local/sbin" the apache2 startup script will be run from your present working directory, if it can be found there, first. In you case, /etc/init.d/.

Whether apache2 is actually in either of these places depends upon your distribution and installations.

---

