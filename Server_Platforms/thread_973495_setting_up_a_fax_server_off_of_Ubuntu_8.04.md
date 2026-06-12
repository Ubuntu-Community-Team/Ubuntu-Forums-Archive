---
title: "setting up a fax server off of Ubuntu 8.04"
date: 2008-11-06
forum: Server Platforms
---

### Post by kustomjs on 2008-11-06
Hi Guys
I just got done installing Ubuntu 8.04 on to a other computer and I want to turn it into a fax server and I am using a old P3 with 384 memory with 80gb hard drive and I am using Agere Systems LT WinModem and I am just wondering how can I get it setup on the server.

---

### Post by kustomjs on 2008-11-06
I am also trying to setup avantfax and I am getting this error:

Warning: require_once(MDB2/Driver/mysql.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/avantfax/includes/SQL.php on line 20

Fatal error: require_once() [function.require]: Failed opening required 'MDB2/Driver/mysql.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/avantfax/includes/SQL.php on line 20

I am also trying to get the address of 206.51.165.11/avantfax and its on 2 different servers how do I get it to work?

---

### Post by kustomjs on 2008-11-07
anybody?

---

### Post by mamut0o1 on 2008-11-14
> **kustomjs said:**
> I am also trying to setup avantfax and I am getting this error:

Warning: require_once(MDB2/Driver/mysql.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/avantfax/includes/SQL.php on line 20

Fatal error: require_once() [function.require]: Failed opening required 'MDB2/Driver/mysql.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/avantfax/includes/SQL.php on line 20

I am also trying to get the address of 206.51.165.11/avantfax and its on 2 different servers how do I get it to work?


Did you install these packages:
apt-get install apache2-mpm-prefork apache2-utils apache2.2-common \
libapache2-mod-php5 libapr1 libaprutil1 libpq4 libsqlite3-0 php5-cli php5-common \
mysql-server imagemagick libtiff4-dev netpbm libnetpbm10-dev libungif-bin \
libungif4-dev sudo postfix php-mail php-mail-mime php-file php-db php5-mysql \
 psutils wdiff

??

---

### Post by rev0lv3r on 2008-11-15
Before you start, have you made sure your Winmodem is compatible with linux?

---

### Post by kevdog on 2008-11-15
LT Winmodems are notoriously hard to get working with linux.  I did for a short time get mine working with the efax package.  There were instructions on the site at that time how to get it working.  A lot of work however had to be done on how to get the LT winmodem working.  It was over a year ago when I did this.  I'm sorry I don't remember the instructions.  Google is your friend.

---

