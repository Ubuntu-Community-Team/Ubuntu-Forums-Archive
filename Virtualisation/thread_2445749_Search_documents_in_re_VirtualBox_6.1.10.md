---
title: "Search documents in re VirtualBox 6.1.10"
date: 2020-06-19
forum: Virtualisation
---

### Post by satimis on 2020-06-19
Hi all,

VirtualBox 6.1.10
Host - Ubuntu 18.04
VMs - Ubuntu 20.04 and 18.04

Could folks here guide me finding VirtualBox document,  Linux host and VMs, particularly;
- Create New Group and delete Group
- Move VMs around on their group and to another group
etc.

Thanks.

What I can find are following 2 documents:
Oracle® VM VirtualBox®
User Manual
Oracle Corporation
Copyright © 2004-2020 Oracle Corporation
[https://www.virtualbox.org/manual/UserManual.html](https://www.virtualbox.org/manual/UserManual.html)

VirtualBox
[https://wiki.archlinux.org/index.php/VirtualBox](https://wiki.archlinux.org/index.php/VirtualBox)

Regards

---

### Post by ajgreeny on 2020-06-19
Sorry but I don't understand what you are wanting to do.

Give us a lot more detail and it may make more sense.

---

### Post by satimis on 2020-06-19
> **ajgreeny said:**
> Sorry but I don't understand what you are wanting to do.

Give us a lot more detail and it may make more sense.
Hi,

I learned a bitter lesson before;

Please see attached Sceenshot-1 and Screenshot-2.

I have no idea how this new group [New group 2] was created. According to my recollection I only tried moving one VM, say VM2, on top of another VM, say VM1 with drag-n-drop.  But a new VM group was then created, "New group 2" automatically.

I expect to find relevant documents in re how to move VMs between groups, say moving VM2, VM6 & VM8 to "New group 2" and moving VM3 on "New group 2" back to "group 1"?  Also how to create new group?

I'm aware it can be done running commands on Terminal.  I have used them before.  Unfortunately I couldn't find respective document on my database.

Thanks

Regards

---

### Post by ajgreeny on 2020-06-19
OK, I've got it now.

In the VBNox main window open up the group containing the VM you want to move and simply drag it, either to the new group or back to the main listing of VMs in the VBox window.

I have never bothered with nor used groups until I saw this thread so I have learned something new this morning.

---

### Post by SeijiSensei on 2020-06-19
I've never used groups either. At most I'll have three or four VMs in my list. Putting them into groups seems superfluous.

---

### Post by satimis on 2020-06-19
> **SeijiSensei said:**
> I've never used groups either. At most I'll have three or four VMs in my list. Putting them into groups seems superfluous.
Hi,

What I'm planning to achieve is as follow;

I have about 40 websites running on Godaddy's server, share hosting.  I'll create their cloned website on local PC.  It's very easy by running "All-in-One Migration" plugin.

I just create a Ubuntu 20.04 VM and install Wordpress on it following below document;
Ubuntu 20.04 Wordpress with Apache installation
[https://linuxconfig.org/ubuntu-20-04-wordpress-with-apache-installation](https://linuxconfig.org/ubuntu-20-04-wordpress-with-apache-installation)
30 April 2020

Afterwards clone 40 VMs.  Then on each website of Godaddy server run "All-in-One Migration" to export the website as .wpress file.  On each VM on local PC just run "All-in-One Migration" to import the respective .wpress file.  After minor adjustment the website is up and can be browsed on local network.  I'm prepared running each website on its own server locally.

Now I have at least 10 cloned websites running on local network without problem.  The websites can be updated/upgraded.  I don't expect running all cloned websites in ONE group.  I'm prepared to run them in 4 groups which is the reason for me creating groups on VM Manager.

Years ago when I was subscribing FIXED IP, I have running following interesting setup;

1) When the cloned websites on local PC were running, visitors browsed the cloned websites
2) When the local PC was switched off, visitors browsed the websites on Godaddy's server.  It was fully automatic and the visitors didn't recognize its change

I can run the cloned websites on a Docker that will be another story.

Maybe I'll re-try the above-mentioned setup again when time allows.  I'm aware Dynamic IP can also work.

I do hope that my explanation above will clarify why I need groups on VM Manager.

Thanks

Regards

---

### Post by SeijiSensei on 2020-06-19
I run multiple WP instances, though not forty of them, on a single virtual machine at Linode using Apache's normal method for handling virtual servers.  I can't imagine running each of them in separate virtual machines. 

There's are native WordPress tools to migrate sites.  I use the WP add-in called [Dupiicator]("https://wordpress.org/plugins/duplicator/") for this task. Simple and effective.

---

### Post by satimis on 2020-06-19
> **SeijiSensei said:**
> I run multiple WP instances, though not forty of them, on a single virtual machine at Linode using Apache's normal method for handling virtual servers.  I can't imagine running each of them in separate virtual machines. 
The advantage having one website on one virtual machine is if there is any wrong I just delete the VM.  It won't affect other websites on the server.  I have plenty of drive space here.

> 
There's are native WordPress tools to migrate sites.  I use the WP add-in called [Dupiicator]("https://wordpress.org/plugins/duplicator/") for this task. Simple and effective.
Thanks.  I'll try it.  Is there a limit on upload file size?

Regards

---

### Post by SeijiSensei on 2020-06-20
There are limits on file upload sizes enforced by PHP (see php.ini).  I don't think WP enforces its own.

Your host must have a lot of memory.  40 virtual machines at, say, 1 GB each is 40 GB of memory.  The amount of overhead in this arrangement is massive.

---

### Post by satimis on 2020-06-24
> **SeijiSensei said:**
>  - snip -
There's are native WordPress tools to migrate sites.  I use the WP add-in called [Dupiicator]("https://wordpress.org/plugins/duplicator/") for this task. Simple and effective.
Hi,

VM - Ubuntu 20.40 Gnome desktop

I am now following below article testing Duplicator to move a website to a VM

How to Migrate a WordPress Site with the Duplicator Plugin
[https://wpshout.com/quick-guides/move-a-wordpress-site-with-the-duplicator-plugin/](https://wpshout.com/quick-guides/move-a-wordpress-site-with-the-duplicator-plugin/)

Now I have following 2 files download```

20200624_mychildhood_79eec7f79405c2886390_20200624085831_archive.daf

installer.php

```

The guide on that article only mentioned not necessary to install WordPress locally.  I suppose needing nginx and php-fpm running on VM to install the above files

$ apt policy nginx php-fpm```

nginx:
  Installed: (none)
  Candidate: 1.17.10-0ubuntu1
  Version table:
     1.17.10-0ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/main amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu focal/main i386 Packages
php-fpm:
  Installed: (none)
  Candidate: 2:7.4+75
  Version table:
     2:7.4+75 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe i386 Packages

```

Please advice.  Thanks

Regards

---

### Post by SeijiSensei on 2020-06-24
I can't help. I use Apache and mod_php on CentOS 6.

But, yes, you'll likely need a web server, PHP, and MySQL.

---

### Post by satimis on 2020-06-29
> **SeijiSensei said:**
> I can't help. I use Apache and mod_php on CentOS 6.

But, yes, you'll likely need a web server, PHP, and MySQL.

Hi all,

Through pain and difficulties and having spent almost 2 days to sort out;
[B]How to migrate a website to a local server with Duplicator plugin.
[/B]
No help from the developer nor having any advice from the wordoress.org forum 

[B][COLOR="#FF0000"]The complete procedure is listed below, in brief;
------------------------------------------------[/COLOR][/B]

Migrate a website, say mywebsite.com, running on Godaddy Server to a local PC.  In my case a VM of Oracle VirtualBox

[B]Step 1
======[/B]
Create a Ubuntu 20.04 desktop VM


[B]Step 2
====[/B]
Following below document to install LAMP Stack;
[COLOR="#FF0000"]How to Install LAMP Stack on Ubuntu 20.04 Server/Desktop[/COLOR]
(LAMP stands for Linux, Apache, MariaDB/MySQL and PHP)
[https://www.linuxbabe.com/ubuntu/install-lamp-stack-ubuntu-20-04-server-desktop](https://www.linuxbabe.com/ubuntu/install-lamp-stack-ubuntu-20-04-server-desktop)


[B]Step 3
====[/B]
**[COLOR="#FF0000"]1)[/COLOR]**
On VM run Firefox to browse mywebsite.com on Internet
and follow below document adding Duplicator plugin;

[COLOR="#FF0000"]**How to Migrate a WordPress Site with the Duplicator Plugin**[/COLOR]
[https://wpshout.com/quick-guides/move-a-wordpress-site-with-the-duplicator-plugin/](https://wpshout.com/quick-guides/move-a-wordpress-site-with-the-duplicator-plugin/)

and to create 2 files;
[B]1. 20200629_website_79eec7f79405c2886390_archive.daf
2. installer.php[/B]
(in my case)


**[COLOR="#FF0000"]2)[/COLOR]**
Download the files to the Downloads folder on VM

[COLOR="#FF0000"]On VM Terminal run following steps:-
[/COLOR]
$ cd Downloads/

$ sudo chown www-data:www-data 20200629_website_79eec7f79405c2886390_archive.daf 
$ sudo chown www-data:www-data installer.php 

$ sudo chmod 777 20200629_website_79eec7f79405c2886390_archive.daf 
$ sudo chmod 777 installer.php 

[B][COLOR="#FF0000"]
2)[/COLOR][/B]
[COLOR="#FF0000"]On VM Terminal run;
[/COLOR]
$ sudo mkdir /var/www/html/satimis-site
$ sudo chown www-data:www-data /var/www/html/satimis-site/

$ sudo mv Downloads/20200629_website_79eec7f79405c2886390_archive.daf /var/www/html/satimis-site/
$ sudo mv Downloads/installer.php /var/www/html/satimis-site/

[B]
Step 4
======[/B]
[COLOR="#FF0000"]Create Database:-
[/COLOR]
On VM Terminal run;

$ sudo mariadb -u root

MariaDB [(none)]> CREATE USER 'satimis'@localhost IDENTIFIED BY 'satimispasswd';
Query OK, 0 rows affected (0.001 sec)

MariaDB [(none)]> CREATE DATABASE satimisDB;

MariaDB [(none)]> SHOW DATABASES;```

+--------------------+
| Database           |
+--------------------+
| satimisDB          |
| information_schema |
| mysql              |
| performance_schema |
+--------------------+
4 rows in set (0.000 sec)
```

MariaDB [(none)]> GRANT ALL PRIVILEGES ON satimisDB.* TO satimis@localhost; 
Query OK, 0 rows affected (0.000 sec)

MariaDB [(none)]> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.000 sec)

MariaDB [(none)]> EXIT
Bye

$ sudo systemctl restart mariadb


[B]Step 5
====[/B]
Following below document migrate mywebsite on VM;

[COLOR="#FF0000"]How to Migrate Your Website With Duplicator[/COLOR]
[https://theme-fusion.com/documentation/avada/how-to/how-to-migrate-your-website-with-duplicator/](https://theme-fusion.com/documentation/avada/how-to/how-to-migrate-your-website-with-duplicator/)
Starting from.... Install / Migrate
-> Until finish

**[COLOR="#FF0000"]On Firefox run;[/COLOR]**
[http://local-ip-address/satimis-site/installer.php](http://local-ip-address/satimis-site/installer.php)

and follow the steps to complete.

[B]
Remark;[/B]
======
I would prefer to run "All-in-One Migrator" Plugin migrating websites.  The steps are much simplier and easier.  The only disadvantage is for websites exceeding 500M in storage size then you have to pay.  

There are solutions on Internet to breakthrough.  I'm not going to mention them here.  Do a hack if you need.

[B]Duplicator plugin
==========[/B]
For large storage websites, it is necessary breaking them to several files before download.  I haven't tested it yet.

Regards

---

