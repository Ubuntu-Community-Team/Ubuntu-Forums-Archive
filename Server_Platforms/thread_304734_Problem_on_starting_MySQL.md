---
title: "Problem on starting MySQL"
date: 2006-11-22
forum: Server Platforms
---

### Post by satimis on 2006-11-22
Hi folks,

Ubuntu-6.06-LAMP-server-amd64

I followed section "10 MySQL" on;
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4)

and found "libmysqlclient12-dev" not installed. After installing it MySQL unabled to start. I reinstalled all packages recommended there.

$ sudo apt-get install --reinstall mysql-server mysql-client libmysqlclient12-dev
Password:```


Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 8 not upgraded.
Need to get 0B/3305kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]?
(Reading database ... 82866 files and directories currently installed.)
Preparing to replace libmysqlclient12-dev 4.0.24-10ubuntu2 (using .../libmysqlclient12-dev_4.0.24-10ubuntu2_amd64.deb) ...
Unpacking replacement libmysqlclient12-dev ...
Preparing to replace mysql-client 5.0.22-0ubuntu6.06.2 (using .../mysql-client_5.0.22-0ubuntu6.06.2_all.deb) ...
Unpacking replacement mysql-client ...
Preparing to replace mysql-server 5.0.22-0ubuntu6.06.2 (using .../mysql-server_5.0.22-0ubuntu6.06.2_all.deb) ...
Unpacking replacement mysql-server ...
Setting up libmysqlclient12-dev (4.0.24-10ubuntu2) ...
Setting up mysql-client (5.0.22-0ubuntu6.06.2) ...
Setting up mysql-server (5.0.22-0ubuntu6.06.2) ...
```

$ sudo /etc/init.d/mysql restart```


Stopping MySQL database server: mysqld...failed.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Killing MySQL database server by signal: mysqld.
Starting MySQL database server: mysqld.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
satimis@ubuntu:~$ /usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
```

Please which file I have to edit getting the problem fixed. TIA


B.R.
satimis

---

### Post by mssever on 2006-11-22
Try ```
sudo dpkg-reconfigure mysql-server
``` If that fails, uninstall and reinstall```
sudo dpkg --purge mysql-server && sudo apt-get install mysql-server
```

---

### Post by mssever on 2006-11-22
Did mysql work before installing libmysqlclient12-dev

If so, then the problem is strange indeed. But you can probably remove it without ill effect. That tutorial tells you to install a lot of stuff I would consider unnecessary. Any package whose name endes in -dev likely falls in that category, unless you plan on compiling software that needs those specific headers. In that case, I would only install what I need.

The list of stuff to install doesnt seem to have been given a lot of thought. For example, they list a bunch of compilation tools, but dont list build-essential, which brings in most of them automatically. Also, they list apt-get, which is already installed on every single Ubuntu system. In fact, if you didnt already have it, you wouldnt be able to run the command line theyre giving in the first place!

---

### Post by satimis on 2006-11-22
Hi mssever,

Tks for your advice.  I haven't tested your advice on #2 yet.  I'm trying to find out the cause in order to learn.

> Did mysql work before installing libmysqlclient12-dev
Yes.  MySQL started without warning.

Now MySQL is running
# netstat -tap | grep mysql```

tcp        0      0 localhost.localdo:mysql *:*                     LISTEN     4837/mysqld
```

But it started with warnings.


> If so, then the problem is strange indeed. But you can probably remove it without ill effect.
I'll remove it later seeing what will happen.

> That tutorial tells you to install a lot of stuff I would consider unnecessary. Any package whose name endes in -dev likely falls in that category, unless you plan on compiling software that needs those specific headers.
To my knowledge .dev is for package development, recompiling, etc.  I just followed their manual.

> The list of stuff to install doesnt seem to have been given a lot of thought. For example, they list a bunch of compilation tools, but dont list build-essential, which brings in most of them automatically. Also, they list apt-get, which is already installed on every single Ubuntu system. In fact, if you didnt already have it, you wouldnt be able to run the command line theyre giving in the first place!
Can I remove them manually?  I'll compare their manual against Ubuntu's removing those packages not listed on the later.  Any additional advice?  What about ISPconfig, is it necessary?  TIA


Edit:
What document will you recommend for fine-tune MySQL.  Google search brought me bundles.  TIA


B.R.
satimis

---

### Post by mssever on 2006-11-22
> **satimis said:**
> Hi mssever,

Tks for your advice.  I haven't tested your advice on #2 yet.  I'm trying to find out the cause in order to learn.


Yes.  MySQL started without warning.

Now MySQL is running
# netstat -tap | grep mysql```

tcp        0      0 localhost.localdo:mysql *:*                     LISTEN     4837/mysqld
```But it started with warnings.

What kind of warnings? Are you able to use MySQL? I generally use phpmyadmin to communicate with mysql as I find it easier.

> To my knowledge .dev is for package development, recompiling, etc.  I just followed their manual.Yes, they're for compiling. You don't need them except when compiling (even running a program that you compiled yourself doesn't require the -dev packages). There's no harm in having them, but I prefer personally to keep an uncluttered systemm only installing dev packages when I need them and uninstalling them when I'm finished.

> Can I remove them manually?  I'll compare their manual against Ubuntu's removing those packages not listed on the later.Yes, you can remove packages anytime. If you try to remove something that is required by another package, you'll get a warning so you don't break your system.>   Any additional advice?  What about ISPconfig, is it necessary?  TIAI don't know anything about ISPconfig. It all depends on what you plan to do as to whether or not you need it. It would be good learning to make sure you understand what a particular package does before installing it--that way you'll have a better grasp of what you're doing. You can get a package description in Synaptic or aptitude--or you can Google.


> Edit:
What document will you recommend for fine-tune MySQL.  Google search brought me bundles.  TIA


B.R.
satimisDo you mean performance tuning? I've never run my own production server, so I haven't really paid attention to that, but I know that there's lots of good documentation on the MySQL website. The default out-of-the-box configuration has worked fine for me--I just changed the interface for mysqld to listen on.

---

### Post by satimis on 2006-11-22
Hi mssever,

> What kind of warnings?

On restart MySQL
$ sudo /etc/init.d/mysql restart```

Stopping MySQL database server: mysqld...failed.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Killing MySQL database server by signal: mysqld.
Starting MySQL database server: mysqld.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
satimis@ubuntu:~$ /usr/bin/mysqladmin: connect to server at 'localhost' failed

error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'

(it hangs here)
```

Utill hitting [Enter] then "satimis@ubuntu:~$" prompted.

It did not indicate whether MySQL started.

However
$ sudo netstat -tap | grep mysql```

tcp        0      0 localhost.localdo:mysql *:*                     LISTEN     7194/mysqld
```
showing MySQL is running.  What is port 7194?

> Are you able to use MySQL?
Not yet, just finishing installing the LAMP-server.  I'm also searching whether a step-by-step testing manual existing.

Others noted with tks.


B.R.
satimis

---

### Post by mssever on 2006-11-22
port 7194 is apparently the port mysql is listening on. To list processes (and see if something's running), type ps -ef | grep search_term. For example, ```
ps -ef | grep mysql
``` will show you all mysql and mysqld processes that are running.

---

### Post by satimis on 2006-11-23
Hi mssever,

> To list processes (and see if something's running), type ps -ef | grep search_term. For example, ```
ps -ef | grep mysql
``` will show you all mysql and mysqld processes that are running.
~$ ps -ef | grep mysql```

root      5742     1  0 20:32 pts/0    00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql     5803  5742  0 20:32 pts/0    00:00:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      5804  5742  0 20:32 pts/0    00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
satimis   5908  5643  0 20:45 pts/0    00:00:00 grep mysql

```

Others noted with tks.

B.R.
satimis

---

### Post by tturrisi on 2006-11-23
Just wondering why that guide says to install libmysqlclient12-dev.  That package is not needed to use mysql databases, it's not a dependancy either. Plus, that guide may be outdated.  I'm running debian etch & the most recent  libmysqlclient-dev package is libmysqlclient15-dev.  I would think Ubuntu used a more recent version.

running this:
apt-get install mysql-server mysql-client libmysqlclient12-dev
will likely install mysql-server 5.x & mysql-client 5.x
while 
libmysqlclient12-dev is a package for mysql-4.x.

Just remove that package, you don't need it for anything.  You may have to purge & remove the server & client, then reinstall them too.

---

### Post by satimis on 2006-11-23
Hi tturrisi,

Tks for your advice.

> running this:
apt-get install mysql-server mysql-client libmysqlclient12-dev
will likely install mysql-server 5.x & mysql-client 5.x
Sorry do I need "libmysqlclient12-dev" here?  OR "libmysqlclient15-dev"?

Shall I remove the existing MySQL first?  What command shall I run to find out its version?

> You may have to purge & remove the server & client, then reinstall them too.
Could you please explain in more detail how to "purge & remove the server & client of MySQL"?  TIA


B.R.
satimis

---

### Post by mssever on 2006-11-23
Try removing libmysqlclient12-dev. If you have to remove mysql-server (I doubt you do), it'll tell you.

To find the versions available, do ```
apt-cache showpkg mysql-server | less
```
To find the version currently installed, type ```
mysqld --version
```
By the way, most programs will give the version number when called with --version.

---

### Post by mssever on 2006-11-23
Removing a package ```
sudo apt-get remove package-name
#or
sudo aptitude remove package-name
``` Uninstalls the package but leaves the configuration files intact (so that if you later reinstall, you;ll have your same settings).

Purging a package ```
sudo aptitude purge package-name
#or
sudo dpkg --purge package-name
``` uninstalls the package and removes the configuration files.

---

