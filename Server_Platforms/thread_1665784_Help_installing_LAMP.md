---
title: "Help installing LAMP"
date: 2011-01-12
forum: Server Platforms
---

### Post by ZenMasta on 2011-01-12
I need to setup a web server. So far not having any success installing anything. ubuntu 10.04.1

I've tried the following from a few online guides.
sudo apt-get install lamp-server^
aptitude install apache2
aptitude install mysql-server mysql-client


each time results in the following

> Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Couldn't find any package whose name or description matched "younameit"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done


This is a virtual server I'm renting. But it was just provisioned so nothing is installed.

My specific needs are
#

    * PHP 5.2.13+
    * Required extensions:
          o PDO_MySQL
          o simplexml
          o mcrypt
          o hash
          o GD
          o DOM
          o iconv
          o curl
          o SOAP (if Webservices API is to be used)
    * Safe_mode off
    * Memory_limit 256

# MySQL:
# SSL:

apt-get install apache2 php5 php5-mcrypt php5-gd php5-curl libapache2-mod-php5 mysql-server mysql-client php5-mysql

---

### Post by memilanuk on 2011-01-12
I think your problem is you're trying to use apt-get to install task names, not package names.

try running 'sudo tasksel' to get a limited gui interface for selecting
different tasks, or 'sudo tasksel install lamp-server' to skip the gui since you know the task name.

Might take a look at the community documentation, specifically this page:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by wongo888 on 2011-01-12
To get started, try the following:

```
$ sudo apt-get install apache2
```

[https://help.ubuntu.com/10.04/serverguide/C/httpd.html#http-installation](https://help.ubuntu.com/10.04/serverguide/C/httpd.html#http-installation)

Then install PHP5:

```
$ sudo apt-get install php5 libapache2-mod-php5
```

[https://help.ubuntu.com/10.04/serverguide/C/php5.html#php5-installation](https://help.ubuntu.com/10.04/serverguide/C/php5.html#php5-installation)

Then install MySQL:

```
$ sudo apt-get install mysql-server
$ sudo apt-get install php5-mysql

```

[https://help.ubuntu.com/10.04/serverguide/C/mysql.html](https://help.ubuntu.com/10.04/serverguide/C/mysql.html)

That 'younameit' package error is very funny. Be careful what you cut and paste off the interwebs.

---

### Post by sj1410 on 2011-01-12
```
sudo tasksel
```

select LAMP & OK

---

### Post by ZenMasta on 2011-01-13
> **wongo888 said:**
> To get started, try the following:
That 'younameit' package error is very funny. Be careful what you cut and paste off the interwebs.

What I meant is you name it... as in no matter which package name I was using, that was going to be whats listed in the error.

tasksel is not available to me, maybe because I'm a virtual server? But then again none of the other commands are working either.

> root@ve:~# sudo tasksel
sudo: tasksel: command not found
root@ve:~# tasksel
bash: tasksel: command not found
root@ve:~# sudo tasksel
sudo: tasksel: command not found
root@ve:~# sudo apt-get install apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package apache2
root@ve:~# sudo apt-get install apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package apache2
root@ve:~# sudo apt-get install php5 libapache2-mod-php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package php5
root@ve:~# sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package mysql-server
root@ve:~# sudo apt-get install php5-mysql
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package php5-mysql


---

### Post by memilanuk on 2011-01-13
Sounds like you have a very limited environment, without quite all of the 'standard' tools and commands installed.  You may want to contact your hosting provider and ask them whats up.

---

### Post by ZenMasta on 2011-01-13
I had to 
apt-get update
apt-get upgrade

then I was able to 
apt-get install apache2 php5 libapache2-mod-php5 mysql-server mysql-client php5-mysql

---

### Post by memilanuk on 2011-01-13
Cool.  Glad you got it working for you.  I still think its a little sketchy that tasksel isn't part of the system, but its mainly just a user-friendly wrapper for apt-get anyways...

---

### Post by weedeater64 on 2011-01-13
Package name vs task name eg.. apache2

First do

```
apt-cache search apache
```
look at the results and inspect packages of interest with,

```
apt-cache show "whatever package you're interested in"
```

where "whatever package you're interested in" is the package name as listed by the search, here is one of the results on my system,

```
**apache2** - Apache HTTP Server metapackage
```

to install or show you need the first part, highlighted above

"apache2"

double clicking that part of the line will copy what you need, then you can paste it after typing either 
apt-cache search
or 
apt-cache show
by center clicking.




to install do

```
apt-get install "package name"
```
where "package name " is the name of the package as listed in the results 
of 

```
apt-cache search
```

---

### Post by James78 on 2011-01-13
If you can install Apache, MySQL, PHP, etc, then you could've installed tasksel too.
```
sudo apt-get install tasksel
sudo tasksel
```

---

