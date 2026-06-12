---
title: "Set Up Server on VirtualBox"
date: 2015-05-09
forum: Virtualisation
---

### Post by alien92 on 2015-05-09
I want to build a Virtual Server on a VM to test Web Applications on. I am aware there are easier methods to test Web apps but I just want to see if this is possible.
I installed Ubuntu 14.04.02LTS on VirtualBox over Windows 8.1.
But now i am totally lost as to what i can do.
I use Oracle for my databases and php and py for backend and want to use the apache framework for the server.
I would appreciate it if someone could guide me for the same.
thanks in advance

---

### Post by deadflowr on 2015-05-09
Moved to Virtualization

---

### Post by SeijiSensei on 2015-05-09
Oracle, huh?  We'll get to that in a minute.

Start the virtual machine from the VirtualBox manager, then log in at the prompt with the username and password you chose during installation.  You should already have working versions of Apache, PHP, and MySQL, I believe.  If you want to use embedded Python scripts you might need an extra Apache module.  Let's update the software on the server and get the needed module.  You'll be running commands as the administrator with the sudo command like this:
```

sudo apt-get update
sudo apt-get upgrade 
sudo apt-get install libapache2-mod-python

```
The first time you use sudo you'll be prompted for your password.  You won't be required to enter it again unless you leave the session idle for a while. The apt-get program handles software management.  The first command tells apt-get to update its current lists of available software "packages;" the second performs an upgrade of the packages already installed.  The third installs the Apache module to enable embedded Python.  I don't know if you need that if you use URLs like [http://example.com/index.py](http://example.com/index.py).

Now let's talk about Oracle.  If all you need to do is connect as a client to a remote server from a PHP application, then you could use Ubuntu Server, but you still have [quite a lot of work]("https://help.ubuntu.com/community/Oracle%20Instant%20Client") to get it set up.  If you want to run your own server instance of Oracle, I don't think you should use Ubuntu at all, but either [Oracle Linux]("http://www.oracle.com/technetwork/server-storage/linux/downloads/default-150441.html") or the clone of RedHat called [CentOS]("http://www.centos.org").  These are the versions of Linux most businesses and enterprises use to run Oracle servers, so you'll find better support if you choose one of those distributions.  From the looks of things, even installing the Oracle server on Oracle Linux appears to be a [fairly complicated task]("http://www.oracle.com/technetwork/articles/servers-storage-admin/ginnydbinstallonlinux-488779.html").

Is Oracle something you need for your job?  If not, I'd suggest switching to an open-source SQL server, either [PostgreSQL]("http://www.postgresql.org") or [MySQL]("http://www.mysql.com/").  Both are easy to install in Ubuntu, and I suspect both can meet all your needs.  I've been writing web applications in PHP with PostgreSQL for over fifteen years. Obviously there's the problem of porting your existing databases, but there is some [help available]("https://wiki.postgresql.org/wiki/Oracle_to_Postgres_Conversion").  I suspect if you're coming from Oracle, Postgres will have a smaller learning curve than MySQL.

To install PostgreSQL, use this command:
```
sudo apt-get install postgresql php5-pgsql
```
The second item is the module that lets you use the [pg_ functions in PHP]("http://php.net/manual/en/book.pgsql.php").

From there, if you decide to stick with Ubuntu, you should peruse the Server Guide, particularly the chapters on [web](https://help.ubuntu.com/lts/serverguide/web-servers.html) and [database](https://help.ubuntu.com/lts/serverguide/databases.html) servers.

---

### Post by TheFu on 2015-05-11
> **alien92 said:**
> 
But now i am totally lost as to what i can do.

I'm totally lost at what you know and what you don't know. 

If you don't know much about Linux, then the learning curve will be extremely steep.  Start with the basics first - be a Linux user.  Become a power-user. Start becoming an Admin and you will be on your way. Start here if you are very new [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) ; 3 hrs of reading will save you hours, days, weeks of frustration.

There are many tools to learn Linux - free online training is available from edx, for example.
You can pay for system admin training if you need to learn it quickly - but there isn't any real substitute for experience. Linux and Unix server administration is mostly learned through mentoring for a few years. At least that has been my experience the last 20 or so years.  There isn't any point-n-click for this. Sorry.

Oh - and as to "what i[sic] can do" - the sky is the limit.  While the **ubuntu server guide** is good, it cannot show/teach all the subtle things necessary to administer a secure server.  The attack vectors change daily, so the knowledge to counter those attacks also changes daily. If you are just playing on an internal network, it is much safer and easier.  Be certain to check out the OWASP guides for writing secure webapps in your language of choice: 
* php [https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet](https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet)
* python [http://www.pythonsecurity.org/](http://www.pythonsecurity.org/)

However, you are free to load up "server", install packages, write code, see what works and have fun doing it.  I've found that postgres is very similar to Oracle from the SW development standpoint. If you don't require Oracle specifically, using pg is the next best thing.

---

