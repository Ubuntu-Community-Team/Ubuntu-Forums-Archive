---
title: "PHP4 installation"
date: 2007-06-23
forum: Server Platforms
---

### Post by Opteron on 2007-06-23
hi

i'm using ubuntu 7.04 server on intel hardware.i have installed apache 2.2.4 from webmin, mysql 5 from apt and trying to compile php from source since it doesnt exist in repositories.

i downloaded php4 from php.net. go to directory and untar it. on the command line ./configure --with-apxs --with-mysql  following occurs:

[B]# ./configure --with-apxs --with-mysql 
loading cache ./config.cache
checking for egrep... grep -E
checking for a sed that does not truncate output... /bin/sed
checking host system type... i686-pc-linux-gnuoldld
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH[/B]

then run make command (which was unavaliable in default install but i added with apt):

[B]make
make: *** No targets specified and no makefile found.  Stop.[/B]

finally run make install:

[B]make install
make: *** No rule to make target `install'.  Stop.[/B]

can someone please help me?

as a side question is there a server related software repository? i have currently enabled universe and multiverse but still apt-get couldnt install php. the mysql there is 5.0 not the latest 5.1. i installed it anyway.

---

### Post by Wardazo on 2007-06-23
Everything's in the synaptic package manager for a basic LAMP instalation

For php 5 

sudo apt-get install apache2 mysql-server mysql-client php5 libapache2-mod-php5 php5-mysql

For php 4

sudo apt-get install apache2 mysql-server mysql-client php4 libapache2-mod-php4 php4-mysql

... you'll need to restart apache

---

### Post by Opteron on 2007-06-23
i have already installed apache and mysql so i run only for php4. 

i run the command apt-get php4

[B]apt-get php4
E: Invalid operation php4[/B]

---

### Post by az on 2007-06-23
Php4 has not been supported for years and so it is no longer in the repositories.

It is still in the Dapper repos.  You can install Dapper and use it there.

Php4 is insecure (and unmaintained) so you should probably avoid it.

---

### Post by Wardazo on 2007-06-23
Hi

> apt-get php4

It's apt-get **install **php5.

The post above states that fiesty no longer supports php4.

---

### Post by Opteron on 2007-06-23
php4 is well maintained and actively supported today now it's 4.4.7.

---

### Post by Opteron on 2007-06-23
[B]apt-get install php4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package php4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package php4 has no installation candidate[/B]

---

### Post by Wardazo on 2007-06-23
> E: Package php4 has no installation candidate

I guess because it's not maintained anymore in the Feisty repository. Try php5 if you can, or

[http://devtime.blogspot.com/2007/05/ubuntu-feisty-doesnt-support-php4.html](http://devtime.blogspot.com/2007/05/ubuntu-feisty-doesnt-support-php4.html)

---

### Post by Opteron on 2007-06-23
thanks but that is not the latest version. do you have any idea on why i didnt accomplish compiling php from source?

---

### Post by az on 2007-06-23
> **Opteron said:**
> php4 is well maintained and actively supported today now it's 4.4.7.

Read this:
[http://www.securityfocus.com/columnists/432](http://www.securityfocus.com/columnists/432)

---

### Post by Wardazo on 2007-06-23
Php5 **is **the latest version of php. Php has two versions at the moment... The php 5 version and the php 4 version for legacy applications. Only php 5 is available on Feisty.

If you really need php 4 it would be a very good idea to move back to ubuntu 6.06 which is a LTS version, as this will make updating very easy and trouble free. Updating php from source, mysql via apt-get and apache, you say you installed it via webmin... well sound like dependancy hell to me.:(

---

### Post by Opteron on 2007-06-23
what i mean is php4 is very very popular you know. simply there are lots of applications which are not compatible with php5. i think that was the major blowup to php usage. 

i probably go with 6.06 but i want to learm how can i compile php.

thanks

---

### Post by circuitjump on 2007-07-05
Hey check this article out. [http://tumbleweed.org.za/2007/06/10/php4-for-feisty-pbuilder-for-beginners/](http://tumbleweed.org.za/2007/06/10/php4-for-feisty-pbuilder-for-beginners/) 

It'll show you how to install it on your feisty machine.

---

