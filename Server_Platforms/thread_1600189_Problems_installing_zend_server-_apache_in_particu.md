---
title: "Problems installing zend server- apache in particular"
date: 2010-10-18
forum: Server Platforms
---

### Post by greengunboat on 2010-10-18
I had installed apache previously on my system, and I think I uninstalled it completely, although remnants might have remained. I have just installed zend server ce php 5.3, and I am having trouble getting it to work. When I log in to the admin interface, it told me it couldn't start the webserver, so I go to restart apache, and it gives me this:


* Starting web server apache2 Syntax error on line 6 of /etc/apache2/sites-enabled/zendserver_gui.conf:
Invalid command 'php_admin_flag', perhaps misspelled or defined by a module not included in the server configuration

This has to do with php_mod some how... but I am not sure how to fix this, or where to start, since I am relatively new to actually setting up apache.  

I thought this might have something to do with libapache2-mod-php... so I went to reinstall it, and ran this:

mburns@mb2449-laptop:~$ sudo aptitude install libapache2-mod-php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages are BROKEN:
libapache2-mod-php-5.3-zend-server
The following NEW packages will be installed:
libapache2-mod-php5 php5-common{a}
0 packages upgraded, 2 newly installed, 0 to remove and 19 not upgraded.
Need to get 0B/3,375kB of archives. After unpacking 8,774kB will be used.
The following packages have unmet dependencies:
libapache2-mod-php-5.3-zend-server: Conflicts: libapache2-mod-php5 but 5.3.2-1ubuntu4.5 is to be installed.
The following actions will resolve these dependencies:

Remove the following packages:
help-zend-server-ce
libapache2-mod-php-5.3-zend-server
zend-server-ce-php-5.3

Score is -463

I did not proceed with uninstalling this...

Can anyone point me in the right direction? Something is messed up with apache, and it is preventing zend server from starting up... any help would be greatly appreciated. Thanks!

P.S. I am using Ubuntu 10.04

---

### Post by minhnghivn on 2010-10-21
Same problem here as I was trying to install php5-cgi
```
administrator@administrator-desktop:/media/DATA/nghi/document$ sudo apt-get install php5-cli php5-common php5-suhosin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
php5-common is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-cli: Depends: php5-common (= 5.3.2-1ubuntu4) but 5.3.2-1ubuntu4.5 is to be installed
E: Broken packages

```

---

### Post by cheenujunk on 2010-11-19
same problem.. does anyone has solution ??

---

