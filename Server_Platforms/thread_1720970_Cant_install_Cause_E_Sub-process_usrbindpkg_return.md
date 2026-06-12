---
title: "Cant install Cause: E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2011-04-03
forum: Server Platforms
---

### Post by Edgar117 on 2011-04-03
I tried installing apache2 & i get this error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
The following packages were automatically installed and are no longer required:
  python-libuser libuser1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 45 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up apache2.2-common (2.2.14-5ubuntu8.4) ...
cp: cannot create regular file `/var/www/index.html': No such file or directory
dpkg: error processing apache2.2-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of apache2-mpm-prefork:
 apache2-mpm-prefork depends on apache2.2-common (= 2.2.14-5ubuntu8.4); however:
  Package apache2.2-common is not configured yet.
dpkg: error processing apache2-mpm-prefork (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apache2:
 apache2 depends on apache2-mpm-worker (= 2.2.14-5ubuntu8.4) | apache2-mpm-prefork (= 2.2.14-5ubuntu8.4) | apache2-mpm-event (= 2.2.14-5ubuntu8.4) | apache2-mpm-itk (= 2.2.14-5ubuntu8.4); however:
  Package apache2-mpm-worker is not installed.
  Package apache2-mpm-prefork is not configured yet.
  Package apache2-mpm-event is not installed.
  Package apache2-mpm-itk is not installed.
 apache2 depends on apache2.2-common (= 2.2.14-5ubuntu8.4); however:
  Package apache2.2-common is not configured yet.
dpkg: error processing apache2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                       No apport report written because MaxReports is reached already
        No apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                                                                                                    of libapache2-mod-php5:
 libapache2-mod-php5 depends on apache2-mpm-prefork (>> 2.0.52) | apache2-mpm-itk; however:
  Package apache2-mpm-prefork is not configured yet.
  Package apache2-mpm-itk is not installed.
 libapache2-mod-php5 depends on apache2.2-common; however:
  Package apache2.2-common is not configured yet.
dpkg: error processing libapache2-mod-php5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5-gd:
 php5-gd depends on phpapi-20090626+lfs; however:
  Package phpapi-20090626+lfs is not installed.
  Package libapache2-mod-php5 which provides phpapi-20090626+lfs is not configured yet.
dpkg: error processing php5-gd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5-mysql:
 php5-mysql depends on phpapi-20090626+lfs; however:
  Package phpapi-20090626+lfs is not installed.
  Package libapache2-mod-php5 which provides phpapi-20090626+lfs is not configured yet.
dpkg: error processing php5-mysql (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apache2.2-common
 apache2-mpm-prefork
 apache2
 libapache2-mod-php5
 php5-gd
 php5-mysql
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help i wanna install LAMPP:popcorn:

---

### Post by falko on 2011-04-04
Do you use the stock /etc/apt/sources.list, or did you modify it?

You might want to try this tutorial: [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.10-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.10-lamp)

---

