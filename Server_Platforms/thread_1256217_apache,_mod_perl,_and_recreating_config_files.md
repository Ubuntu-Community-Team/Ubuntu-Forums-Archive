---
title: "apache, mod_perl, and recreating config files"
date: 2009-09-02
forum: Server Platforms
---

### Post by supremedalek on 2009-09-02
I am having a problem with apache2 in my ubuntu 9.04 server. I was trying to get RT installed and it was barking it could not find mod_perl. After fidgeting with it, I decided to remove apache and RT and then focus on getting apache with mod_perl happy. I did

```
dalek@ubuntu:~$ sudo apt-get remove --purge apache2 libapache2-mod-perl2 libdbd-pg-perl libapache-dbi-perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdevel-symdump-perl libdigest-sha1-perl apache2-mpm-worker libapr1
  apache2-utils apache2.2-common libbsd-resource-perl ssl-cert libperl5.10
  libpq5 libaprutil1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apache2* libapache-dbi-perl* libapache2-mod-perl2* libapache2-reload-perl*
  libdbd-pg-perl*
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 4932kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 37591 files and directories currently installed.)
Removing libapache-dbi-perl ...
Removing libapache2-reload-perl ...
Removing libapache2-mod-perl2 ...
egrep: /etc/apache2/mods-enabled/*.load: No such file or directory
Module perl already disabled
Purging configuration files for libapache2-mod-perl2 ...
Removing apache2 ...
Removing libdbd-pg-perl ...
Processing triggers for man-db ...
dalek@ubuntu:~$
```

Then I reinstalled all those packages. When I checked /etc/apache2, it only created the mods-available directory, which contained perl.load and nothing else. 

```
dalek@ubuntu:~$ sudo apt-get install apache2 libapache2-mod-perl2 libdbd-pg-perl libapache-dbi-perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libapache2-reload-perl
The following NEW packages will be installed:
  apache2 libapache-dbi-perl libapache2-mod-perl2 libapache2-reload-perl
  libdbd-pg-perl
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1480kB of archives.
After this operation, 4932kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Selecting previously deselected package apache2.
(Reading database ... 37163 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.11-2ubuntu2.3_all.deb) ...
Selecting previously deselected package libapache2-mod-perl2.
Unpacking libapache2-mod-perl2 (from .../libapache2-mod-perl2_2.0.4-5ubuntu1_amd64.deb) ...
Selecting previously deselected package libapache-dbi-perl.
Unpacking libapache-dbi-perl (from .../libapache-dbi-perl_1.07-1_all.deb) ...
Selecting previously deselected package libapache2-reload-perl.
Unpacking libapache2-reload-perl (from .../libapache2-reload-perl_0.10-2_all.deb) ...
Selecting previously deselected package libdbd-pg-perl.
Unpacking libdbd-pg-perl (from .../libdbd-pg-perl_2.11.7-1_amd64.deb) ...
Processing triggers for man-db ...
Setting up apache2 (2.2.11-2ubuntu2.3) ...
Setting up libapache2-mod-perl2 (2.0.4-5ubuntu1) ...
Enabling module perl.
Could not create /etc/apache2/mods-enabled/perl.load: No such file or directory

Setting up libapache-dbi-perl (1.07-1) ...
Setting up libapache2-reload-perl (0.10-2) ...
Setting up libdbd-pg-perl (2.11.7-1) ...
dalek@ubuntu:~$ ls /etc/apache2/
mods-available
dalek@ubuntu:~$ 
```

What am I doing wrong here? I thought a reinstall of apache2 would force /etc/apache2 to be recreated and repopulated.

---

### Post by supremedalek on 2009-09-02
Problem seems to be solved; I needed to have apache2.2-commons installed.

---

