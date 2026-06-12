---
title: "i cant get xampp to work on mu ubuntu 9.10"
date: 2010-04-24
forum: Server Platforms
---

### Post by Edgar09 on 2010-04-24
Hello linux pros
I cant get to my phpmyadmin on xampp 
I tried doing it on the terminal but i get this wierd message

XAMPP: Another web server daemon is already running.
XAMPP: Another MySQL daemon is already running.
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

But i cant get in phpmyadmin

What can i do linux pros?:confused:

---

### Post by windependence on 2010-04-24
Most likely you have Apache and mySQL already installed and running and now you're trying to install again over what is there. 

Post the output of:

```
sudo ps aux | grep httpd
sudo ps aux | grep mysqld
```

That will tell us if you have Apache and MySQL already running and you can then kill those processes before you install if need be.

-Tim

---

### Post by Edgar09 on 2010-04-25
o.k i get thus on the terminal:


edgar88@edgar88-laptop:~$ sudo ps aux | grep httpd
[sudo] password for edgar88: 
edgar88   8982  0.0  0.0   4116   800 pts/0    R+   14:30   0:00 grep --color=auto httpd
edgar88@edgar88-laptop:~$ sudo ps aux | grep mysqld
root      1115  0.0  0.0   1748   452 ?        S    Apr24   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     1263  0.0  0.1 145588  1764 ?        Sl   Apr24   0:05 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306
root      1264  0.0  0.0   1664   480 ?        S    Apr24   0:00 logger -t mysqld -p daemon.error
edgar88   8989  0.0  0.0   4120   884 pts/0    R+   14:30   0:00 grep --color=auto mysqld

---

### Post by windependence on 2010-04-26
You definitely have MySQL already installed. Any reason for XAMPP over say just installing the normal LAMP stack on Ubuntu? It's super easy.

-Tim

---

### Post by Edgar09 on 2010-04-26
Well Tim i got the answer on my own but thanks any way
The answer was sooooo easy

sudo /etc/init.d/mysql stop

Then u go to the xampp panel & execute MYSQL
:lolflag:

 -Edgar

---

### Post by windependence on 2010-04-27
Unless you stop the other MySQL instance from starting, you are going to have this problem every time you restart this machine. You will need to remove the other startup script from the machine to avoid conflicts in the future.

-Tim

---

