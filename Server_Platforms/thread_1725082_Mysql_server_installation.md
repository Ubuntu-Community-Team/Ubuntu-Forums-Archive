---
title: "Mysql server installation"
date: 2011-04-09
forum: Server Platforms
---

### Post by thoufiq on 2011-04-09
I have just 20 days of experience in Linux.I am installing mysql server in ubuntu 10.10 (32-bit) server without using internet. From mysql home page, i had downloaded .deb files and .tar.gz files but i cant install these files. It shows error like this

osm-client@osmclient-HP:~$ cd MySql
osm-client@osmclient-HP:~/MySql$ ls
mysql-workbench-gpl-5.2.33b-1ubu1004-i386(2).deb
mysql-workbench-gpl-5.2.33b-1ubu1010-i386(2).deb
osm-client@osmclient-HP:~/MySql$ sudo su
[sudo] password for osm-client: 
root@osmclient-HP:/home/osm-client/MySql# sudo dpkg --install mysql-workbench-gpl-5.2.33b-1ubu1004-i386\(2\).deb 
(Reading database ... 124011 files and directories currently installed.)
Preparing to replace mysql-workbench-gpl 5.2.33-1ubu1004 (using mysql-workbench-gpl-5.2.33b-1ubu1004-i386(2).deb) ...
Unpacking replacement mysql-workbench-gpl ...
dpkg:dependency problem preven configuration of mysql-workbench-gpl:
mysql-workbench-gpl depends on libgnome2-0 (>= 2.17.3); however:
package libgnome2-0 is not installed.
mysql-workbench-gpl depends on libmysqlclient16 (>= 5.1.21.1); however:
package libmysqlclient16 is not installed.
dpkg: error processing mysql-workbench-gpl (--install)
dependency problems - leaving unconfigured
Errors were encountered while processing:
mysql-workbench-gpl

Is this possible to install mysql server manually without using internet????
If possible, what are all the commands i should use to install.

Any advice????????

---

### Post by falko on 2011-04-09
You must download and install libgnome2-0 and libmysqlclient16 as well. You can download them from [http://packages.ubuntu.com](http://packages.ubuntu.com) , but please note that these packages again might have some unresolved dependencies.

---

### Post by thoufiq on 2011-04-09
> **falko said:**
> You must download and install libgnome2-0 and libmysqlclient16 as well. You can download them from [http://packages.ubuntu.com](http://packages.ubuntu.com) , but please note that these packages again might have some unresolved dependencies.


Hello falko,
                      Thanks for your valuable suggestion. But again while installing libmysqlclient16, it shows error like this

dpkg: regarding libmysqlclient16_5.1.49-1ubuntu8.1_i386.deb containing libmysqlclient16:
mysql-cluster-client-5.1 conflicts with libmysqlclient16
libmysqlclient16 (version 5.1.49-1ubuntu8.1) is to be installed.
dpkg: error processing libmysqlclient16_5.1.49-1ubuntu8.1_i386.deb (--install)
conflicting packages - not installing libmysqlclient16
Errors were encountered while processing:
libmysqlclient16_5.1.49-1ubuntu8.1_i386.deb

---

### Post by thoufiq on 2011-04-11
> **thoufiq said:**
> Hello falko,
                      Thanks for your valuable suggestion. But again while installing libmysqlclient16, it shows error like this

dpkg: regarding libmysqlclient16_5.1.49-1ubuntu8.1_i386.deb containing libmysqlclient16:
mysql-cluster-client-5.1 conflicts with libmysqlclient16
libmysqlclient16 (version 5.1.49-1ubuntu8.1) is to be installed.
dpkg: error processing libmysqlclient16_5.1.49-1ubuntu8.1_i386.deb (--install)
conflicting packages - not installing libmysqlclient16
Errors were encountered while processing:
libmysqlclient16_5.1.49-1ubuntu8.1_i386.deb



Any Suggestions???

---

### Post by Ryan Dwyer on 2011-04-11
Sounds like you need APTonCD!

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by coeus82 on 2011-04-27
It looks like mysql-workbench-gpl is missing two dependencies. To fix this issue you must first do the following:

```
sudo apt-get install libzip1 python-pysqlite2
```

After, install workbench and it should work (it worked for me).

---

