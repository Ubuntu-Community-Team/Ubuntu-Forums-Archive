---
title: "php5-mysql package problem"
date: 2008-03-31
forum: Server Platforms
---

### Post by mvan83 on 2008-03-31
I'm running a server that must use php5 along with mysql 4.1. Both are up and running along with apache 2. Trying to connect to the db from php fails. So I try to install php5-mysql, but I get the following error:
The following packages have unmet dependencies:
  php5-mysql: Depends: libmysqlclient15off (>= 5.0.27-1) but it is not going to be installed

Ok. Trying to install that along with it says I must install mysql-common version 5.0 or greater. But php5-mysql can work with mysql 4.1. Here's the description for it:
Description: MySQL module for php5
 This package provides modules for MySQL database connections directly from
 PHP scripts.  It includes the generic "mysql" module which can be used
 to connect to all versions of MySQL, an improved "mysqli" module for
 MySQL version 4.1 or later, and the pdo_mysql module for use with
 the PHP Data Object extension.

So obviously it doesn't really need mysql 5, but by dependency on a dependency, it claims it does. Any way to get around this? (I thought dependency hell went the way of the dodo about 4 years ago...apparently not - just adds to the long list of reasons that I loathe mysql and php).

Thanks for any help you can offer.

---

### Post by egonzalez on 2008-03-31
My friend,

Have you tried to make a LAMP (Linux, Apache,  MySQL, PHP) install from scratch? It can take you about 15 minutes and can save you from headaches...

You can run this inatallation from the Ubuntu Server CD during the installation process.

I hope this helps.

---

### Post by mvan83 on 2008-03-31
Thanks for the response. Unfortunately that's not an option. This is a development server for an existing machine running those versions of mysql and php.

---

