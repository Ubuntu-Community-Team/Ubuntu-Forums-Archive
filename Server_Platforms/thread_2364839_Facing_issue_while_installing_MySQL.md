---
title: "Facing issue while installing MySQL"
date: 2017-06-28
forum: Server Platforms
---

### Post by lakshminarayanan3 on 2017-06-28
Hi All,

I am new to MySQL. I installed MySQL 5.7 on Ubuntu 16.04.2 LTS but forgot the root password set. I tried several ways to reconfigure, but unlucky. So decided to remove and install it again.

For removing MySQL packages, I executed the following:

sudo apt-get remove mysql*
sudo apt-get autoremove
sudo apt-get autoclean
sudo rm -rf /var/lib/mysql
sudo rm -rf /etc/mysql

Then, I was trying to do a fresh install by

sudo apt-get update
sudo apt-get install mysql-server

and I am hitting the following error

Setting up mysql-common (5.7.18-0ubuntu0.16.04.1) ...
update-alternatives: error: alternative path /etc/mysql/my.cnf.fallback doesn't exist
dpkg: error processing package mysql-common (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 mysql-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

I guess, me removing /etc/mysql is leading to this.

Please help in getting MySQL installed.

Thanks
N.Lakshminarayanan

---

### Post by TheFu on 2017-06-28
Advice: Don't remove files installed by the package manager from outside the package manager. If you want to remove everything in an install (except data files, which are never removed), use "apt-get purge". 

Try to force the install.  **sudo apt-get -f install mysql-server**

Just want to mention you might want to use mariaDB instead of MySQL.  MariaDB isn't from Oracle which might be enough to convince you to change.  All client access and program names are compatible with mysql, so it is just the server that is different.  Treat it just like mysql, but without the ties to Oracle.  MariaDB is from the original makers of mysql who decided to leave Oracle after the SunMicro purchase. They've been around in their new company long enough that we know they make a superior, compatible, DBMS.  Of course, it is always your choice which to use, which is something fantastic about F/LOSS.

---

### Post by howefield on 2017-06-28
Moved to "*Server Platforms*" forum for a better fit.

---

### Post by lakshminarayanan3 on 2017-06-29
Hi,

Thanks for your reply. Let me try force install and update you.

Regarding your advice, yes I will follow in future.

On the MariaDB, let me explore it. I do not have a specific choice to tie to MySQL. I may migrate my setup to my Windows laptop.

Thanks
N.Lakshminarayanan

---

### Post by darkod on 2017-06-29
It is too late now but you should know it for the future. There is a procedure to reset a forgotten mysql root password. You shouldn't have tried to reinstall mysql right away. You should have googled little more...

---

### Post by staylorui on 2017-06-29
I had the same problem and it helped to uninstall both mysql-server and mysql-client via

[FONT=courier new]**sudo apt-get remove --purge mysql-\***[/FONT]

And then install mysql-server and mysql-client with

[B][FONT=courier new]sudo apt-get install mysql-server mysql-client


[/FONT][/B]

---

