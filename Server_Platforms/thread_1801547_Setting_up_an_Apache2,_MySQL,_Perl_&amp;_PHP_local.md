---
title: "Setting up an Apache2, MySQL, Perl &amp; PHP localhost?"
date: 2011-07-10
forum: Server Platforms
---

### Post by UltraNEO* on 2011-07-10
Hi there, I'm completely new to Ubuntu and would like some help getting started. 
I'm aware there a Mac forum but this issue really isn't just for Mac, is it?

For the time being I'm running Ubuntu 10.10 on a Macbook 4,1 with all the most recent patches, so far everything appears to be working well. Being happy I thought I'd move things along and start setting up the web-server assuming it's possible with the desktop version. In an ideal world I like to run the web-server using the system based **Apache2** also need access to **Perl**, **CGI** and **PHP** development environments instead of applications such as LAMP/MAMP. 

So after some searching I've found a tutorial but come across an unexpected problem, something way outta my depth. Have search for a solution but nothing cut throat. Have just opened up the terminal:

```
$ sudo apt-get install apache2
``` 
after entering my PW it give me:> 
[sudo] password for ultraneo: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


 I'm baffled, what does it mean? Initially thought it's got something to do with the application I had opened, so I've since terminated them all and tried again.. with the CD in the drive for good measure. But no, it's still the same :( 

Anyone like to give me a working guide for setting this up?

---

### Post by wojox on 2011-07-10
It means you have more than one package manager open. Like Synaptic, Ubuntu Software Center. Make sure those are closed. Last case scenario, reboot.

---

### Post by UltraNEO* on 2011-07-10
> **wojox said:**
> It means you have more than one package manager open. Like Synaptic, Ubuntu Software Center. Make sure those are closed. Last case scenario, reboot.

Ahh.. Many Thanks. 

Have rebooted, re-ran the command and it appears to have installed. 
For the record, is there a task manager so I can see what applications remain open? Could be useful.

---

### Post by UltraNEO* on 2011-07-10
[INDENT] **Now I'm installing PHP5..**
[/INDENT]```
$ sudo apt-get install libapache2-mod-php5
```[INDENT]**Then create links to apache2**
[/INDENT]```
$ sudo a2enmod php5
```[INDENT]**Restart Apache2:**
[/INDENT]```
$ sudo service apache2 restart
```Open browser, key in 127.0.0.1 hit return:

> **It works!**

 This is the default web page for this server.
 The web server software is running but no content has been added, yet.
[INDENT]**Install MYSQL with PHP 5**
[/INDENT]```
$ sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql
```[B][COLOR=Red]

[/COLOR][/B]**[COLOR=Red]Wait.. [/COLOR]**

[COLOR=Blue][COLOR=Black]Why do I install PHP5 in twice?
Was there a quicker shorter way of doing all of this?[/COLOR]
[/COLOR][COLOR=Black]
[/COLOR]

---

### Post by brighty22 on 2011-07-10
> **UltraNEO* said:**
> For the record, is there a task manager so I can see what applications remain open? Could be useful.

So to System -> Administration -> System Monitor

> **UltraNEO* said:**
> Was there a quicker shorter way of doing all of this?

The php5-mysql package is required for php5 to interact with mysql. Most packages have dependencies - other packages they require to work properly. For example it would be pointless to have the bit of php that can interact with mysql, without the other libraries php needs to work. Apt-get worries about all of this for you, and will install any dependencies for a package if they are not installed already. Read more about php5-mysql and its dependencies [here]("http://packages.ubuntu.com/maverick/php5-mysql").

For your mysql problem, try

```
mysql -u root -p
```

and then type in you password. Oh wait, you've edited it.. but I'll leave it in for anyone else who finds this thread :)

---

### Post by UltraNEO* on 2011-07-10
> For your mysql problem, try

```
mysql -u root -p
```and then type in you password. Oh wait, you've edited it.. but I'll leave it in for anyone else who finds this thread :)

Sorry, I realized my error and corrected it with some password resetting :)

---

### Post by UltraNEO* on 2011-07-10
**Question**... 

Where on the HD is the root webserver directory?

---

### Post by UltraNEO* on 2011-07-10
> **UltraNEO* said:**
> **Question**... 

Where on the HD is the root webserver directory?

Nevermind, I found it... :P

---

### Post by UltraNEO* on 2011-07-10
OK.. Weird. 

Sorry for being a noob.. :(
What's the best way to install **phpMyAdmin**? I tried the most ovbious one..

```
$ sudo apt-get install phpmyadmin
```

but it's telling me this... 

> [sudo] password for ultraneo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package phpmyadmin

Does that mean there's an error? or something else opened?

---

### Post by wojox on 2011-07-10
You need to turn on the universe repositories.

---

### Post by UltraNEO* on 2011-07-10
> **wojox said:**
> You need to turn on the universe repositories.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=197191&stc=1&d=1310349117[/IMG]

Hmm... OK.. I think according this, they are.. right?


I ended up restarting (again) and entering... lol

```
$ sudo apt-get update
$ sudo apt-get install phpmyadmin
$ sudo apt-get install mysql-admin

```OK.. Not done this before, did that actually install phpMyAdmin or just set up the server for it?

---

### Post by wojox on 2011-07-10
What did it say in the terminal? What if you go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

### Post by UltraNEO* on 2011-07-10
> **wojox said:**
> [COLOR=Red]What did it say in the terminal?[/COLOR] 

What it say? 

```
$ sudo apt-get update
```> Get:1 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198B]
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en      
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]                     
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en    
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg [198B]          
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en   
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_GB
Get:4 [http://archive.canonical.com](http://archive.canonical.com) maverick Release [5,925B]         
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_GB [94.5kB]
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_GB           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Get:6 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources [3,994B]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                      
Get:7 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages [6,680B]    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en  
Get:8 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_GB [91.2kB]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en 
Get:9 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_GB [2,332B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Get:10 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_GB [32.0kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg [198B]  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_GB
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_GB
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release [39.8kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release [31.4kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release [31.4kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources [829kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources [4,370B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources [4,179kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources [151kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main amd64 Packages [1,491kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted amd64 Packages [6,002B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe amd64 Packages [5,771kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse amd64 Packages [180kB]    
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources [135kB]         
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources [778B]    
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe Sources [46.3kB]    
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse Sources [2,506B]  
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main amd64 Packages [374kB]  
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted amd64 Packages [1,802B]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe amd64 Packages [152kB]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse amd64 Packages [5,074B]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main Sources [44.6kB]       
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted Sources [14B]    
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe Sources [18.8kB]   
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse Sources [1,758B] 
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main amd64 Packages [152kB] 
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted amd64 Packages [14B]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe amd64 Packages [73.9kB]
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse amd64 Packages [3,618B]
Fetched 14.0MB in 8s (1,594kB/s)                                               
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?```
$ sudo apt-get update
```> Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en  
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_GB 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_GB
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg           
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_GB
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                   
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse amd64 Packages
Reading package lists... Done```
$ sudo apt-get install phpmyadmin
```> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dbconfig-common javascript-common libapache2-mod-php5 libjs-mootools
  libmcrypt4 php5-cli php5-common php5-gd php5-mcrypt php5-mysql
  wwwconfig-common
Suggested packages:
  php-pear libmcrypt-dev mcrypt php5-suhosin postgresql-client apache
  apache-ssl
The following NEW packages will be installed
  dbconfig-common javascript-common libjs-mootools libmcrypt4 php5-gd
  php5-mcrypt phpmyadmin wwwconfig-common
The following packages will be upgraded:
  libapache2-mod-php5 php5-cli php5-common php5-mysql
4 upgraded, 8 newly installed, 0 to remove and 16 not upgraded.
Need to get 12.0MB of archives.
After this operation, 21.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main dbconfig-common all 1.8.46 [474kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe wwwconfig-common all 0.2.1 [22.8kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe javascript-common all 7 [3,854B]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main php5-cli amd64 5.3.3-1ubuntu9.5 [3,020kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main php5-mysql amd64 5.3.3-1ubuntu9.5 [75.6kB]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libapache2-mod-php5 amd64 5.3.3-1ubuntu9.5 [3,107kB]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main php5-common amd64 5.3.3-1ubuntu9.5 [566kB]
Get:8 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe libjs-mootools all 1.2.4.0~debian1-1 [248kB]
Get:9 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe libmcrypt4 amd64 2.5.8-3.1 [87.6kB]
Get:10 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main php5-gd amd64 5.3.3-1ubuntu9.5 [38.7kB]
Get:11 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe php5-mcrypt amd64 5.3.3-0ubuntu2 [18.6kB]
Get:12 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe phpmyadmin all 4:3.3.7-5build0.10.10.1 [4,342kB]
Fetched 12.0MB in 6s (1,983kB/s)                                               
Preconfiguring packages ...
Selecting previously deselected package dbconfig-common.
(Reading database ... 148337 files and directories currently installed.)
Unpacking dbconfig-common (from .../dbconfig-common_1.8.46_all.deb) ...
Selecting previously deselected package wwwconfig-common.
Unpacking wwwconfig-common (from .../wwwconfig-common_0.2.1_all.deb) ...
Selecting previously deselected package javascript-common.
Unpacking javascript-common (from .../javascript-common_7_all.deb) ...
Preparing to replace php5-cli 5.3.3-1ubuntu9 (using .../php5-cli_5.3.3-1ubuntu9.5_amd64.deb) ...
Unpacking replacement php5-cli ...
Preparing to replace php5-mysql 5.3.3-1ubuntu9 (using .../php5-mysql_5.3.3-1ubuntu9.5_amd64.deb) ...
Unpacking replacement php5-mysql ...
Preparing to replace libapache2-mod-php5 5.3.3-1ubuntu9 (using .../libapache2-mod-php5_5.3.3-1ubuntu9.5_amd64.deb) ...
Unpacking replacement libapache2-mod-php5 ...
Preparing to replace php5-common 5.3.3-1ubuntu9 (using .../php5-common_5.3.3-1ubuntu9.5_amd64.deb) ...
Unpacking replacement php5-common ...
Selecting previously deselected package libjs-mootools.
Unpacking libjs-mootools (from .../libjs-mootools_1.2.4.0~debian1-1_all.deb) ...
Selecting previously deselected package libmcrypt4.
Unpacking libmcrypt4 (from .../libmcrypt4_2.5.8-3.1_amd64.deb) ...
Selecting previously deselected package php5-gd.
Unpacking php5-gd (from .../php5-gd_5.3.3-1ubuntu9.5_amd64.deb) ...
Selecting previously deselected package php5-mcrypt.
Unpacking php5-mcrypt (from .../php5-mcrypt_5.3.3-0ubuntu2_amd64.deb) ...
Selecting previously deselected package phpmyadmin.
Unpacking phpmyadmin (from .../phpmyadmin_4%3a3.3.7-5build0.10.10.1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up dbconfig-common (1.8.46) ...

Creating config file /etc/dbconfig-common/config with new version
Setting up wwwconfig-common (0.2.1) ...
Setting up javascript-common (7) ...
Setting up php5-common (5.3.3-1ubuntu9.5) ...
Installing new version of config file /etc/cron.d/php5 ...
Setting up php5-cli (5.3.3-1ubuntu9.5) ...
Setting up libapache2-mod-php5 (5.3.3-1ubuntu9.5) ...
Action 'configtest' failed.
The Apache error log may have more information.
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.confu.

Creating config file /etc/dbconfig-common/phpmyadmin.conf with new version

Creating config file /etc/phpmyadmin/config-db.php with new version
granting access to database phpmyadmin for phpmyadmin@localhost: success.
verifying access for phpmyadmin@localhost: success.
creating database phpmyadmin: success.
verifying database phpmyadmin exists: success.
populating database via sql...  done.
dbconfig-common: flushing administrative password
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place```
$ sudo apt-get install mysql-admin
```> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mysql-gui-tools-common mysql-query-browser
The following NEW packages will be installed
  mysql-admin mysql-gui-tools-common mysql-query-browser
0 upgraded, 3 newly installed, 0 to remove and 16 not upgraded.
Need to get 3,935kB of archives.
After this operation, 12.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe mysql-gui-tools-common all 5.0r14+openSUSE-2.1 [320kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe mysql-admin amd64 5.0r14+openSUSE-2.1 [1,892kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe mysql-query-browser amd64 5.0r14+openSUSE-2.1 [1,723kB]
Fetched 3,935kB in 3s (1,118kB/s)              
Selecting previously deselected package mysql-gui-tools-common.
(Reading database ... 149584 files and directories currently installed.)
Unpacking mysql-gui-tools-common (from .../mysql-gui-tools-common_5.0r14+openSUSE-2.1_all.deb) ...
Selecting previously deselected package mysql-admin.
Unpacking mysql-admin (from .../mysql-admin_5.0r14+openSUSE-2.1_amd64.deb) ...
Selecting previously deselected package mysql-query-browser.
Unpacking mysql-query-browser (from .../mysql-query-browser_5.0r14+openSUSE-2.1_amd64.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up mysql-gui-tools-common (5.0r14+openSUSE-2.1) ...
Setting up mysql-admin (5.0r14+openSUSE-2.1) ...
Setting up mysql-query-browser (5.0r14+openSUSE-2.1) ...> **wojox said:**
> What if you go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

After restarting the server and visiting localhost, it give me the login page for phpMyAdmin as expected. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=197199&stc=1&d=1310355344[/IMG]

Yay!! My very first install of Apache, MySql & Php on Linux. 

Change the permissions and take ownership of[COLOR=Red] **[COLOR=Black]/[/COLOR]var[COLOR=Black]/[/COLOR]www**[/COLOR] I used:

```
$ sudo chown -R $USER:$USER /var/www
```i can drop files into the folder without it moaning... 


OK.... 
To prove it works... 
Log into phpMyAdmin and create a wordpress database, for argument sakes, I left my collation on default.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=197205&stc=1&d=1310357867[/IMG]

To prove it works, i downloaded [wordpress]("http://wordpress.org") from source..  unzipped and manually dropped it into [COLOR=Red] **[COLOR=Black]/[/COLOR]var[COLOR=Black]/[/COLOR]www**[/COLOR] 
Open a new tab, open firefox's* add-on* page and search for [FireFTP]("http://fireftp.mozdev.org/").   Find the webserver root and chmod the Wordpress directory to 0777  giving it permission to write the 'config.php'

[SIZE=3][SIZE=2]Hmm.. think I should try to activate the ftp. if my logic serves me correctly by default there's no FTP server pre-installed? What's good?? Or what will work for me?[/SIZE][/SIZE]

---

### Post by UltraNEO* on 2011-07-11
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=197212&stc=1&d=1310359964[/IMG]

Soooo.. Now I'm stumped. 
What do i need to make this go away ??

---

### Post by UltraNEO* on 2011-07-11
[COLOR=Red]*trash Wordpress, drop the db*[/COLOR]



Now the fun part... 
How to get CPAN to install, preferably **DBD::mysql  ** work. I've not have a clue... :confused:

*goes googling for an hour...*

---

### Post by UltraNEO* on 2011-07-11
> **UltraNEO* said:**
> [COLOR=Red]*trash Wordpress, drop the db*[/COLOR]



Now the fun part... 
How to get CPAN to install, preferably **DBD::mysql  ** work. I've not have a clue... :confused:

*goes googling for an hour...*


Meh.. I'm such a smart ***, I've solved it!!!

Thanks to everyone who've help me along the way, couldn't of done it with your input.

---

