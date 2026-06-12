---
title: "The following packages have unmet dependencies:"
date: 2010-12-12
forum: Server Platforms
---

### Post by sierd on 2010-12-12
sierd@ubuntu:~$ sudo apt-get install phpmyadmin 
[sudo] password for sierd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 phpmyadmin : Depends: dbconfig-common but it is not installable
              Recommends: apache2 or
                          lighttpd but it is not going to be installed or
                          httpd
              Recommends: php5-gd but it is not going to be installed
              Recommends: mysql-client
E: Broken packages


How can i fix this

---

### Post by Vegan on 2010-12-12
```
sudo tasksel install lamp
```

---

### Post by karthick87 on 2010-12-12
Run,

```
sudo apt-get update
```

If you get any errors during update,post the entire output here in code tags.

---

### Post by sierd on 2010-12-12
```
sierd@ubuntu:~$ sudo apt-get update 
[sudo] password for sierd: 
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release
Hit http://us.archive.ubuntu.com maverick Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://security.ubuntu.com maverick-security/main Sources
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-backports Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_US
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release
Hit http://us.archive.ubuntu.com maverick-updates Release
Hit http://us.archive.ubuntu.com maverick-backports Release
Hit http://us.archive.ubuntu.com maverick/main Sources
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main Sources
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-backports/main Sources
Hit http://us.archive.ubuntu.com maverick-backports/restricted Sources
Hit http://us.archive.ubuntu.com maverick-backports/universe Sources
Hit http://us.archive.ubuntu.com maverick-backports/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-backports/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-backports/multiverse i386 Packages
Reading package lists... Done

```

---

### Post by karthick87 on 2010-12-12
Now install the package,
```

sudo apt-get install phpmyadmin
```

---

### Post by sierd on 2010-12-12
Then again I get the same output as before and i did ```
sudo apt-get install-f
``` but that didn't repaired it

---

### Post by wojox on 2010-12-12
You still need to install LAMP as stated above. phpmyadmin is a front end for mysql written in php.

---

### Post by karthick87 on 2010-12-12
First install the following,

```
sudo apt-get install apache2 php5 php5-mysql mysql-server
```

and then,
```

sudo apt-get install phpmyadmin
```

---

### Post by sierd on 2010-12-12
Normaly when I install phpmyadmin it install mysql, php and apache2 with it

---

### Post by sierd on 2010-12-12
```
sierd@ubuntu:~$ sudo apt-get install apache2 php5 php5-mysql mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apache2 : Depends: apache2-mpm-worker (= 2.2.16-1ubuntu3.1) but it is not going to be installed or
                    apache2-mpm-prefork (= 2.2.16-1ubuntu3.1) but it is not going to be installed or
                    apache2-mpm-event (= 2.2.16-1ubuntu3.1) but it is not going to be installed or
                    apache2-mpm-itk (= 2.2.16-1ubuntu3.1) but it is not going to be installed
           Depends: apache2.2-common (= 2.2.16-1ubuntu3.1) but it is not going to be installed
 mysql-server : Depends: mysql-server-5.1 but it is not going to be installed
E: Broken packages

```

---

### Post by karthick87 on 2010-12-12
No it wont install,have you tried??

---

### Post by sierd on 2010-12-12
yes but it shows the same

---

### Post by wojox on 2010-12-12
```
sudo tasksel install lamp-server
```

[ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by sierd on 2010-12-12
@wojox
 that will not fix my apt-get problem i think and i want to install more than phpmyadmin and a webserver

---

### Post by wojox on 2010-12-12
Run

```
sudo apt-get clean
```

```
sudo apt-get -f install
```

---

### Post by sierd on 2010-12-13
Try it doesn't work :(

---

### Post by sierd on 2010-12-13
I fixxed it :D

first i installed dbconfig-common by hand (i don't know if apt-get uses it but after that it workt again)
than i put ```
deb http://nl.archive.ubuntu.com/ubuntu maverick main

``` in to the source.list file and i update with ```
apt-get update
``` and every thing was working again :D

---

### Post by bagesh2050 on 2011-11-01
Hi, i tried this and worked on my machine - 

sudo aptitude install apache2

after running it whatever it ask just say no to those questions. and if if not runs then may choose yes option at last.

Then it will install apache2 on your machine.

---

### Post by nothingspecial on 2011-11-01
Halloween was yesterday.

Please don't bump old threads to the top.

Closed.

---

