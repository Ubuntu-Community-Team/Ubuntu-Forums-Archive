---
title: "Install some apps on server."
date: 2009-06-25
forum: Server Platforms
---

### Post by crzyone9584 on 2009-06-25
My VPS is running Ubuntu Jaunty as its server. I' trying to install the following.

> apache2-common
libapache2-mod-php4
libperl5.8
libsasl2
libsnmp-session-perlappt
mysql-client-4.1
mysql-common-4.1
mysql-server-4.1
php4
php4-gd
php4-mcrypt
php4-mysql
php4-pear
proftpd-mysql

When i try to install them I get this error. 

"name of software" has no installation candidate

I was wondering if there is a way to get htem installed. im working through ssh.

---

### Post by Bachstelze on 2009-06-25
PHP 4 isn't supported in Ubuntu anymore, so you can't install it through the official repositories. As for the other packages, please paste the exact command you're running, and the exact output you're getting.

---

### Post by crzyone9584 on 2009-06-25
I jsut realize some of them give you a package that will replace the ones im trying to install Ill give you an update after i try the replacements.

here is a few things that dont work 

> apt-get install libapache2-mod-php4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libapache2-mod-php4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache2-mod-php4 has no installation candidate


> apt-get install libsnmp-session-perlappt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libsnmp-session-perlappt


> apt-get install mysql-client-4.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mysql-client-4.1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mysql-client-4.1 has no installation candidate


> apt-get install mysql-common-4.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mysql-common-4.1


> apt-get install mysql-server-4.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mysql-server-4.1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  mysql-server-5.1
E: Package mysql-server-4.1 has no installation candidate


> apt-get install php4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package php4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package php4 has no installation candidate

As you said php 4 is not supported in ubuntu any more. So would 5 be able to run if so what version is the latest php and is everyhting that is listed bleow in php5 be able to install

> php4
php4-gd
php4-mcrypt
php4-mysql
php4-pear

> apt-get install proftpd-mysql 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package proftpd-mysql is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package proftpd-mysql has no installation candidate


---

### Post by cariboo on 2009-06-26
Instead of trying to install the packages individually, why not use tasksel?

```
sudo tasksel
```

Then select LAMP from the menu.

---

### Post by crzyone9584 on 2009-06-26
this is what i get

>  sudo tasksel
sudo: tasksel: command not found


---

### Post by juancarlospaco on 2009-06-26
**sudo apt-get update ; sudo apt-get install tasksel && sudo tasksel**

---

### Post by crzyone9584 on 2009-06-26
i did this ealier before i went to work

sudo apt-get install lamp-server^

seems to work fine. everything seems to be installed ok. just need to get my control panel up and running now. thanks for the help guys.

---

### Post by Kareeser on 2009-06-26
Indeed, installing from the meta-packages is infinitely easier than installing and configuring everything by hand.

I suspect your original commands were for outdated versions of software.

---

