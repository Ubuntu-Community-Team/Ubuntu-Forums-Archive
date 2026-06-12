---
title: "apache2 uninstall"
date: 2007-07-12
forum: Server Platforms
---

### Post by Daveyboy on 2007-07-12
anyone know why after installing apache2 with apt-get and then removing apache2 with 'apt-get remove --purge apache2' and rebooting it is still running?

---

### Post by FKi on 2007-07-12
ha, yeah im having the same problems.im trying to uninstall it and reinstall because the default files got messed around with, and im trying to restore teh defaults, but it seems uninstalling does nothing, couse after uninstalling its still runnin and all the files are still there

:S

---

### Post by Footballkid4 on 2007-07-12
Is apache2 still running, or is httpd running?  httpd (which is apache I believe, but under a different name), is preinstalled on a lot of linux distributions.  You might want to try:
```
sudo apt-get remove httpd --purge httpd
```

@FKi: if you want to reinstall the defaults, then:
```
sudo apt-get install --reinstall apache2
```
Should clear all .conf files and reinstall with the defaults.

---

### Post by Railsbuntu on 2008-01-24
Hi I have a similar problem.

Phpmyadmin was messing with me about a secret passphrase, so I tried uninstalling/reinstalling it, but it didn't change anything. And I saw that apache2 thing that always showed up when reinstalling, so I decided to uninstall apache2 (I want to fully switch to nginx), so I uninstalled apache2 using all possible methods described in this thread.

Then I uninstalled/reinstalled phpmyadmin, and that idiot keeps coming up with an error message about trying to restart apache, and some apache.conf file missing.

a:
> locate apache2
Tells me that apache2 is still hanging around and has not been removed althoug apt-get disagrees.

What the hell is wrong with apache2??? :confused:

---

