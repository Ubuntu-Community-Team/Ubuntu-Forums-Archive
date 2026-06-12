---
title: "Having trouble removing apache2"
date: 2010-01-29
forum: Server Platforms
---

### Post by timClicks on 2010-01-29
```
$ sudo apt-get purge apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libterm-readline-perl-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apache2*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 36.9kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 246519 files and directories currently installed.)
Removing apache2 ...
$ /etc/init.d/apache2 status
 * Apache is running (pid 21327).
```


Can anyone make sense of this?

---

### Post by hemimaniac on 2010-01-29
did you try 

sudo /etc/init.d/apache2 stop

then try to remove it, packages don't like being jerked out if they are running, may also need to kill anything depending on it

---

### Post by timClicks on 2010-01-29
Looks like that's helped! Thanks :)

---

