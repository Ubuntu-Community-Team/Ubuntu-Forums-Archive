---
title: "[SOLVED] Problem with Apache Virtual Hosts"
date: 2008-05-30
forum: Server Platforms
---

### Post by ashkev on 2008-05-30
My Apache was working, and somehow I messed things up.  I have my site in /var/www.  Now when I try to restart Apache I get this error:

* Starting apache 2.0 web server... [Fri May 30 12:07:31 2008] [warn] module cgi_module is already loaded, skipping
[Fri May 30 12:07:31 2008] [warn] module perl_module is already loaded, skipping[Fri May 30 12:07:31 2008] [warn] module php5_module is already loaded, skipping[Fri May 30 12:07:31 2008] [warn] module userdir_module is already loaded, skipping
[Fri May 30 12:07:31 2008] [warn] The Alias directive in /etc/apache2/apache2.conf at line 351 will probably never match because it overlaps an earlier Alias.
[Fri May 30 12:07:31 2008] [warn] The Alias directive in /etc/apache2/sites-enabled/squirrelmail at line 1 will probably never match because it overlaps an earlier Alias.
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

What should I do?

Thanks

---

### Post by Titan8990 on 2008-05-30
I had a similar problem a while back. Ended up reformatting the system. Hope somebody has some insight on the problem for you.

---

### Post by quelx on 2008-05-30
It's telling you there are still **apache2** threads running try ```
sudo killall apache2
```

make a backup of your /etc/apache2 folder maybe ```
sudo cp -r /etc/apache2 /etc/apache2.20080530
```

then ```
sudo dpkg-reconfigure apache2
```

then ```
sudo /etc/init.d/apache2 restart
```

---

### Post by ashkev on 2008-05-30
Well, I tried what you suggested, but the results are the same:

kevin@ubuntu-webserver:~$ sudo killall apache2
Password:
apache2: no process killed
kevin@ubuntu-webserver:~$ sudo cp -r /etc/apache2 /etc/apache2.20080530
kevin@ubuntu-webserver:~$ sudo dpkg-reconfigure apache2
kevin@ubuntu-webserver:~$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server... [Fri May 30 13:26:55 2008] [warn] module cgi_module is already loaded, skipping
[Fri May 30 13:26:55 2008] [warn] module perl_module is already loaded, skipping[Fri May 30 13:26:55 2008] [warn] module php5_module is already loaded, skipping[Fri May 30 13:26:55 2008] [warn] module userdir_module is already loaded, skipping
[Fri May 30 13:26:55 2008] [warn] The Alias directive in /etc/apache2/apache2.conf at line 351 will probably never match because it overlaps an earlier Alias.
[Fri May 30 13:26:55 2008] [warn] The Alias directive in /etc/apache2/sites-enabled/squirrelmail at line 1 will probably never match because it overlaps an earlier Alias.
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

---

### Post by turinglabs on 2008-05-30
Could be a couple of things. The error "Address already in use: make_sock: could not bind to address [::]:80" means you have something bound to port 80 already, probably an old instance of Apache that did not shutdown cleanly. Do a normal shutdown, then look for any Apache processes still hanging around. If they are there, kill them off:

sudo /etc/init.d/apache2 stop
ps ax | grep apache2

...and if you see any remaining:

sudo pkill -f apache2

Then start Apache again and see what happens.

---

### Post by ashkev on 2008-05-30
No Change....

> kevin@ubuntu-webserver:~$ sudo /etc/init.d/apache2 stop
 * Stopping apache 2.0 web server...                                     [ ok ]
kevin@ubuntu-webserver:~$ ps ax | grep apache2
10005 pts/0    S+     0:00 grep apache2
kevin@ubuntu-webserver:~$ sudo pkill -f apache2
kevin@ubuntu-webserver:~$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server... [Fri May 30 13:37:48 2008] [warn] module cgi_module is already loaded, skipping
[Fri May 30 13:37:48 2008] [warn] module perl_module is already loaded, skipping[Fri May 30 13:37:48 2008] [warn] module php5_module is already loaded, skipping[Fri May 30 13:37:48 2008] [warn] module userdir_module is already loaded, skipping
[Fri May 30 13:37:48 2008] [warn] The Alias directive in /etc/apache2/apache2.conf at line 351 will probably never match because it overlaps an earlier Alias.
[Fri May 30 13:37:48 2008] [warn] The Alias directive in /etc/apache2/sites-enabled/squirrelmail at line 1 will probably never match because it overlaps an earlier Alias.
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

---

### Post by quelx on 2008-05-30
```
sudo netstat -l|grep www
```

please post your replies in [PHP]```

```[/PHP] brackets so the text doesn't get turned into smilies :) (see the **#** symbol on the editor bar)

---

### Post by ashkev on 2008-05-30
It doesn't look like anything happened.```
kevin@ubuntu-webserver:~$ sudo netstat -l|grep www
kevin@ubuntu-webserver:~$

```

---

### Post by quelx on 2008-05-30
okay well you've got a backup of your config files right?

if so do try this ```
sudo **apt-get** --purge remove apache2
sudo rm -rf /etc/apache2/
sudo apt-get install apache2
```

Use your old conf files as guides but don't simply copy them back into the **/etc/apache2** folder, carefully use this guide for recreating your virtual servers

[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)

---

### Post by tonkyman on 2008-05-30
When you say you messed it up what exactly did you do??

Was it running fine and just started acting up or did you add a new software package and it stop working. Did you edit apache2.conf?? I noticed a line in your message that says line 351 in /etc/apache2/apache2.conf has an error. Under Apache2 never edit the apache2.conf file.

I had issues like this with my new server but it ended up being a bad virtualhost setting with a new site I installed. 

Tony

---

### Post by ashkev on 2008-05-30
It didn't like the --purge thing...
 ```
root@ubuntu-webserver:/home/kevin# sudo --purge remove apache2
sudo: please use single character options
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
```

---

### Post by ashkev on 2008-05-30
> **tonkyman said:**
> When you say you messed it up what exactly did you do??

Was it running fine and just started acting up or did you add a new software package and it stop working. Did you edit apache2.conf?? I noticed a line in your message that says line 351 in /etc/apache2/apache2.conf has an error. Under Apache2 never edit the apache2.conf file.

I had issues like this with my new server but it ended up being a bad virtualhost setting with a new site I installed. 

Tony

I am not sure what I did.  It was working.  All that I rember doing was removing certain files and folders from /var/www in an attempt to clean things up on the server.  I also have webmin installed, and it is possible that I inadvertantly changed something while trying to see what was in there...   I really can't tell you what I might have done.  I didn't realize that things were bad until the following day when I saw that there was no website there...  

Luckily I had a backup server that I moved the website to....

BTW this is all running on vmware... don't think that should make a difference, but I thought that I would mention it.

---

### Post by ashkev on 2008-05-30
> **quelx said:**
> okay well you've got a backup of your config files right?

if so do try this ```
sudo --purge remove apache2
sudo rm -rf /etc/apache2/
sudo apt-get install apache2
```

Use your old conf files as guides but don't simply copy them back into the **/etc/apache2** folder, carefully use this guide for recreating your virtual servers

[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)
```
kevin@ubuntu-webserver:~$ sudo apt-get --purge remove apache2
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  apache2*
0 upgraded, 0 newly installed, 1 to remove and 71 not upgraded.
Need to get 0B of archives.
After unpacking 81.9kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 61224 files and directories currently installed.)
Removing apache2 ...
kevin@ubuntu-webserver:~$ sudo rm -rf /etc/apache2/
kevin@ubuntu-webserver:~$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 71 not upgraded.
Need to get 0B/36.2kB of archives.
After unpacking 81.9kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 61223 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.0.55-4ubuntu2.3_i386.deb) ...
Setting up apache2 (2.0.55-4ubuntu2.3) ...
kevin@ubuntu-webserver:~$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server... awk: cannot open /etc/apache2/apache2.conf (No such file or directory)
grep: /etc/apache2/apache2.conf: No such file or directory
                                                                         [fail]
kevin@ubuntu-webserver:~$
```

Doesn't it install a default apache2.conf?

---

### Post by quelx on 2008-05-30
it does, or rather it is supposed to, what does ```
ls -l /etc/apache2/
``` show

---

### Post by ashkev on 2008-05-30
> **quelx said:**
> it does, or rather it is supposed to, what does ```
ls -l /etc/apache2/
``` show

```
kevin@ubuntu-webserver:~$ ls -l /etc/apache2/
ls: /etc/apache2/: No such file or directory
kevin@ubuntu-webserver:~$

```

---

### Post by quelx on 2008-05-30
okay I'm at a loss, you could try ```
sudo apt-get --reinstall install apache2
```or it looks like the apt-get --purge remove/install cycle worked for someone before:

[http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2006-10/msg00783.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2006-10/msg00783.html)

---

### Post by ashkev on 2008-05-30
Very strange isn't it....  

I tried to uninstall and install again, with no luck...

```

root@ubuntu-webserver:/home/kevin# apt-get remove --purge apache2
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  apache2*
0 upgraded, 0 newly installed, 1 to remove and 71 not upgraded.
Need to get 0B of archives.
After unpacking 81.9kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 61224 files and directories currently installed.)
Removing apache2 ...
root@ubuntu-webserver:/home/kevin# apt-get install apache2
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 71 not upgraded.
Need to get 0B/36.2kB of archives.
After unpacking 81.9kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 61223 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.0.55-4ubuntu2.3_i386.deb) ...
Setting up apache2 (2.0.55-4ubuntu2.3) ...
root@ubuntu-webserver:/home/kevin# ls -l /etc/apache2/
ls: /etc/apache2/: No such file or directory
```

---

### Post by spiderbatdad on 2008-05-30
looks like you are looking for /etc/apache2 in /home/kevin...that wouldn't work.

> /home/kevin# ls -l /etc/apache2/
ls: /etc/apache2/: No such file or directory

EDIT: my bad. it does work.

---

### Post by quelx on 2008-05-30
I know there was an update to **apache2** since Hardy's release, also noticed you have 71 packages awaiting updates... probably unrelated but if you are in fact running Hardy, do a ```
sudo apt-get dist-upgrade
```

---

### Post by ashkev on 2008-05-30
> **quelx said:**
> I know there was an update to **apache2** since Hardy's release, also noticed you have 71 packages awaiting updates... probably unrelated but if you are in fact running Hardy, do a ```
sudo apt-get dist-upgrade
```

Boy sorry... I totally forgot to mention that this is a Ubuntu 6.06.2 LTS (Dapper Drake)

---

### Post by ashkev on 2008-05-30
So I tried:
```
sudo apt-get --purge remove apache2-common
```

Then 

```
sudo apt-get install apache2 apache2-common
```

And now I have:

```
root@ubuntu-webserver:/home/kevin# ls -l /etc/apache2/
total 72
-rw-r--r-- 1 root root 12482 2008-02-04 14:59 apache2.conf
drwxr-xr-x 2 root root  4096 2008-05-30 16:00 conf.d
-rw-r--r-- 1 root root   748 2008-02-04 14:49 envvars
-rw-r--r-- 1 root root   268 2008-05-30 16:00 httpd.conf
-rw-r--r-- 1 root root 12441 2008-02-04 14:59 magic
drwxr-xr-x 2 root root  4096 2008-05-30 16:00 mods-available
drwxr-xr-x 2 root root  4096 2008-05-30 16:00 mods-enabled
-rw-r--r-- 1 root root    10 2008-05-30 16:00 ports.conf
-rw-r--r-- 1 root root  2266 2008-02-04 14:59 README
drwxr-xr-x 2 root root  4096 2008-05-30 16:00 sites-available
drwxr-xr-x 2 root root  4096 2008-05-30 16:00 sites-enabled
drwxr-xr-x 2 root root  4096 2008-02-04 14:59 ssl
root@ubuntu-webserver:/home/kevin# 

```

So hopefully, I will be able to recreate the config files etc.

Thanks for all of the help

---

