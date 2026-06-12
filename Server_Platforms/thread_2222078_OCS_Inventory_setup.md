---
title: "OCS Inventory setup"
date: 2014-05-05
forum: Server Platforms
---

### Post by 49jBlJpaCkw8 on 2014-05-05
Hi, 

I just wanted to solicit an advice on how to setup OCS inventory in Ubuntu.  I'm always hitting a wall in the setup.  BTW, I'm a Windows user which is learning in Linux (Ubuntu) but my knowledge is mostly GUI. Now that said, I'm setting it up on vmware for testing, however, due to my units' limitation, I am only limited to use 32-bit and as such, I have no choice but to try it on Trusty's 32-bit desktop.

Everytime I installed it via 
sudo apt-get install ocsinventory-server ocsinventory-reports
I can not access the [http://localhost/ocsreports](http://localhost/ocsreports) (or with /install.php).  The error is something like "the requested URL /ocsreports was not found on this server"

I apache2 is working because of the system because as I can see a webpage which says that Apache is working.  

As such I can not continue to configure it and test it with GLPI (which I have successfully installed earlier in another VM...I'm also planning to install GLPI alongside OCS Inventory).

Thank you so much for the anticipated support.

---

### Post by jonobr on 2014-05-05
Maybe your installation path is changed or wrong?
Try searching for install.php

sudo find / -name install.php 
maybe its somewhere else

---

### Post by SeijiSensei on 2014-05-05
If you're using 14.04, the default website directory has changed from /var/www to /var/www/html.  If you have a /var/www/html directory and a /var/www/ocsreports directory, try moving ocsreports below /var/www/html.

---

### Post by 49jBlJpaCkw8 on 2014-05-05
@jonobr, I've tried to use locate command and the path is correct.

---

### Post by 49jBlJpaCkw8 on 2014-05-05
Thaks @SeijiSensei.  While i have a /var/www/html directory, I have no other directory in /var/www (like /ocsreports).  Earlier testing also does not have other directories other than the /www.  Besides, another (virtual) test which successfully installed glpi also does not contain anything in /var/www.

Again, thank you both for taking time to analyze and help me out.

---

### Post by SeijiSensei on 2014-05-06
I installed both ocsinventory-server and ocs-inventory-reports and looked at the list of included files with "dpkg -L package-name".  I didn't see anything that connected this program to Apache.  The whole application is written in Perl and is installed in /usr/lib/perl5.  Apache's mod-perl is also installed, but I didn't see any other modifications made to the Apache configuration.

When I browsed down the list of files in ocsinventory-reports, I saw that lots of things were installed to /usr/share/ocsinventory-reports including install.php and index.php.  So I tried a little experiment:

1)  I edited (as root with sudo) the file /etc/apache2/sites-available/000-default.conf and added the line
```
Alias /ocsreports /usr/share/ocsinventory-reports
```
just above the closing "</VirtualHost>" directive.  

2)  I restarted Apache with "sudo service apache2 restart".

3)  I pointed the browser on this machine to [http://localhost/ocsreports](http://localhost/ocsreports).  I got the installation form for the application.

Adding the alias tells Apache where to find the files for the /ocsreports URI.  I don't understand why the package didn't install itself correctly to Apache.  Looks like a bug to me.  There are three bugs filed against ocsinventory-reports at [Launchpad]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=ocsinventory-reports&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=").  None of them are this bug, and all of them are pretty old.  I might file a bug for this problem if I have a chance, though there isn't much to indicate that this package is well-supported by Ubuntu.

---

### Post by 49jBlJpaCkw8 on 2014-05-06
@SeijiSensei, thank you so much on going all through the hassel of installing and checking for the error I've encountered, its well appreciated.  It's people like (and jonobr and a couple of other helpful guys) you which makes linux easier for windows folks like me.  

Will be trying your solution in a while.

---

### Post by 49jBlJpaCkw8 on 2014-05-06
Yup...the Alias line did the trick.  Again, thank you so much...will now continue with testing.

---

### Post by koenn on 2014-05-07
> **SeijiSensei said:**
> 
Adding the alias tells Apache where to find the files for the /ocsreports URI.  I don't understand why the package didn't install itself correctly to Apache.  Looks like a bug to me.  
More precisely : a bug in the  packaging of ocsinventory for Ubuntu 14.04

I've been running glpi and ocsinventory for a while now on 12.04 and I am actually anticipating this sort of trouble with "universe" packages that depend on lamp when upgrading to 14.04. 

re the file locations : debian package maintainers tend to use /var/lib/<package name> and /usr/share/>package name> or similar locations for LAMP applications, rather than /var/www. That's why you did not find any files  at first. Their aim is to keep program files  outside the  document root.

the site definition for ocsinventory  (12.04 package) lives in /etc/apache2/conf.d  (and actually symlinks back to /etc/ocsinventory/ocsreports.conf). It contains a.o. the Alias directives to point ocsinventory url's to the appropriate paths

As I understand it, in the 14.04 Apache version, the use of apache conf.d is obsoleted. The ocsinventory package for 14.04 should handle that change; but apparently it doesnt, at least not entirely correctly.

---

### Post by vhinz on 2014-05-15
Thank you for your inputs...actually, I was the OP, I requested my name changed because I mis-set-up my account last year.  

Back to the topic, I would also like to add that RackTables also needs the "Alias" workaround for it to work.  

Many thanks to all who took time to help me out and those who replied.

---

