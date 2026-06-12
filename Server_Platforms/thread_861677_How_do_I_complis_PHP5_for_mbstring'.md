---
title: "How do I complis PHP5 for mbstring'?"
date: 2008-07-16
forum: Server Platforms
---

### Post by YouBunn2 on 2008-07-16
I'm a noob and donut know much about compiling PHP with mbstring emabled. Can someone walk me through the process?

Ubuntu Linux 8.04.1
PHP Version 5.2.4-2ubuntu5.2


TIA.

---

### Post by RealPSL on 2008-07-16
Have you checked to make sure Ubuntu does not already ship with the mbstring enabled? You can tell from the phpinfo.php output. Either way below is one example of compiling with mbstring enabled.

[http://www.php.net/manual/en/install.unix.apache2.php]("http://www.php.net/manual/en/install.unix.apache2.php")

In the step that says 

```
./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql
```

Change it to

```
./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql --enable-mbstring
```

Note that you do not have to recompile Apache to do this you can just specify the correct path to apxs. Again I would strongly recommend that you review the phpinfo.php output to make sure Ubuntu does not enable mbstring before you compile yourself. If you compile you will have to recompile each time there is a problem.

---

### Post by mikepeters76 on 2010-03-11
Did you resolve this issue?

I am running:
lsb_release -rd
Description:	Ubuntu 8.04.1
Release:	8.04

and I am trying to get apxs installed so I can compile mod_security but I get the following error:

sudo apt-get install apxs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apxs
michael@michael-laptop:~/Downloads/modsecurity-apache_2.5.12/apache2$ sudo apt-get install httpd-devel
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: Couldn't find package httpd-devel
michael@michael-laptop:~/Downloads/modsecurity-apache_2.5.12/apache2$ sudo apt-get install httpd-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package httpd-dev
michael@michael-laptop:~/Downloads/modsecurity-apache_2.5.12/apache2$ sudo apt-get install apache2-dev
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Note, selecting apache2-threaded-dev instead of apache2-dev
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  apache2-threaded-dev: Depends: apache2.2-common (= 2.2.8-1) but 2.2.8-1ubuntu0.5 is to be installed
                        Depends: libaprutil1-dev but it is not going to be installed
E: Broken packages


There was a bug opened about it but it was closed without a real resolution???

Thanks in advance.  Is there a way to force the install of httpd-devel?

---

