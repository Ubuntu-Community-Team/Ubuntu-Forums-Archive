---
title: "apache2 php5 mysql problems"
date: 2010-09-02
forum: Server Platforms
---

### Post by spillage2 on 2010-09-02
Hi 

I have installed apahce2, php5 and mysql but seem to have messed things up.

What would be the best way to fully remove these programmes and restart the installation for ubuntu 10.04.

Fairly new to linux so any dummies guide would be a help.

Thanks,

Spill.

---

### Post by spillage2 on 2010-09-02
seem to be having a problem removing phpmyadmin

sudo apt-get purge libapache2-mod-auth-mysql phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libapache2-mod-auth-mysql is not installed, so not removed
The following packages will be REMOVED
  phpmyadmin*
0 upgraded, 0 newly installed, 1 to remove and 9 not upgraded.
1 not fully installed or removed.
After this operation, 17.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 158878 files and directories currently installed.)
Removing phpmyadmin ...
.: 5: Can't open /usr/share/dbconfig-common/dpkg/prerm.mysql
dpkg: error processing phpmyadmin (--purge):
 subprocess installed pre-removal script returned error exit status 2
.: 35: Can't open /usr/share/dbconfig-common/dpkg/postinst.mysql
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by de0xyrib0se on 2010-09-02
Are you sure no other 'apt-get' are running?

---

### Post by spillage2 on 2010-09-02
no there wasn't.

im hoping i have removed everything through synaptics and have install vbox to test my stuff on in future rather than muck around with my main settings.

i am just about to try and install apache again to check.

---

### Post by spillage2 on 2010-09-03
last night i used synaptic to remove apache2 php5 and mysql but still get this is i try to reinstall apache2.

sudo apt-get install apache2
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnet-daemon-perl libhtml-template-perl libdbi-perl libplrpc-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-mpm-worker apache2-utils apache2.2-bin apache2.2-common
Suggested packages:
  apache2-doc apache2-suexec apache2-suexec-custom
The following NEW packages will be installed
  apache2 apache2-mpm-worker apache2-utils apache2.2-bin apache2.2-common
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3,075kB of archives.
After this operation, 9,425kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package apache2.2-bin.
(Reading database ... 159560 files and directories currently installed.)
Unpacking apache2.2-bin (from .../apache2.2-bin_2.2.14-5ubuntu8_i386.deb) ...
Selecting previously deselected package apache2-utils.
Unpacking apache2-utils (from .../apache2-utils_2.2.14-5ubuntu8_i386.deb) ...
Selecting previously deselected package apache2.2-common.
Unpacking apache2.2-common (from .../apache2.2-common_2.2.14-5ubuntu8_i386.deb) ...
Selecting previously deselected package apache2-mpm-worker.
Unpacking apache2-mpm-worker (from .../apache2-mpm-worker_2.2.14-5ubuntu8_i386.deb) ...
Selecting previously deselected package apache2.
Unpacking apache2 (from .../apache2_2.2.14-5ubuntu8_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up apache2.2-bin (2.2.14-5ubuntu ...
Setting up apache2-utils (2.2.14-5ubuntu ...
Setting up apache2.2-common (2.2.14-5ubuntu ...
ERROR: Module reqtimeout does not exist!
dpkg: error processing apache2.2-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of apache2-mpm-worker:
 apache2-mpm-worker depends on apache2.2-common (= 2.2.14-5ubuntu; however:
  Package apache2.2-common is not configured yet.
dpkg: error processing apache2-mpm-worker (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apache2:
 apache2 depends on apache2-mpm-worker (= 2.2.14-5ubuntu | apache2-mpm-prefork (= 2.2.14-5ubuntu | apache2-mpm-event (= 2.2.14-5ubuntu | apache2-mpm-itk (= 2.2.14-5ubuntu; however:
  Package apache2-mpm-worker is not configured yet.
  Package apache2-mpm-prefork is not installed.
  Package apache2-mpm-event is not installed.
  Package apache2-mpm-itk is not installed.
 apache2 depends on apache2.2-common (= 2.2.14-5ubuntu; however:
  Package apache2.2-common is not configured yet.
dpkg: error processing apache2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        Errors were encountered while processing:
 apache2.2-common
 apache2-mpm-worker
 apache2
E: Sub-process /usr/bin/dpkg returned an error code (1)

any help would be appreciated

---

### Post by de0xyrib0se on 2010-09-03
apt-get update

sudo dpkg --purge --force-remove-reinstreq apache2.2-common

apt-get install apache2

---

### Post by spillage2 on 2010-09-03
thank you very much worked a treat.

---

### Post by mickeoliver on 2010-09-26
I had exactly the same problem, and that solution worked for me too. 

But now I'm having trouble installing php:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libapache2-mod-php5
Suggested packages:
  php-pear
The following NEW packages will be installed:
  libapache2-mod-php5 php5
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/2,989kB of archives.
After this operation, 8,507kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libapache2-mod-php5.
(Reading database ... 167453 files and directories currently installed.)
Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.3.2-1ubuntu4.5_amd64.deb) ...
Selecting previously deselected package php5.
Unpacking php5 (from .../php5_5.3.2-1ubuntu4.5_all.deb) ...
Setting up libapache2-mod-php5 (5.3.2-1ubuntu4.5) ...
Not replacing deleted config file /etc/php5/apache2/php.ini

Setting up php5 (5.3.2-1ubuntu4.5) ...

```

I seem to have deleted php.ini or something...

---

### Post by spillage2 on 2010-09-28
I had an issue with php working and also getting aptana to work correctly. spent hours on it then just left it for a day.

when i came back to comp it was all working correctly.......

---

