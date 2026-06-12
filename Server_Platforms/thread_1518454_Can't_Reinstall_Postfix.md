---
title: "Can't Reinstall Postfix"
date: 2010-06-26
forum: Server Platforms
---

### Post by Devin82m on 2010-06-26
Hello, 

I have Ubuntu Server 10.04 and I follow the guide on HowToForge:

[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04)

I tried going through the guide twice without success. So I uninstalled almost everything that the guide instructed me to install. Well I figured out what my stupid mistake was, I used example.com instead of my domain name throughout the entire process. Well I decided to try it all again but kept getting strange errors when I tried reinstalling Postfix. Now I figured that the reason why was because I went through every directory and deleted anything related to Postfix I could find. (Before when I couldn't get it to work is when I did this) None the less here is what apt-get says when I try to reinstall or do anything related to Postfix, even when I run apt-get upgrade.

_**Here is an example of what ```
apt-get upgrade
``` gives me:**_

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up postfix (2.7.0-1) ...
update-rc.d: /etc/init.d/postfix: file does not exist
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)


_**This is what ```
apt-get install -f
``` gives me:**_

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dictionaries-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postfix (2.7.0-1) ...
update-rc.d: /etc/init.d/postfix: file does not exist
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)


If anyone has any ideas please let me know. I am at a loss. I wish I could flush apt-get or something so that it doesn't look for those files or directories. Even if I could install Postfix over the top of the old one that would be great. Then I could run the configuration afterwords. Thanks!

---

### Post by lisati on 2010-06-26
Something to try before reinstalling:
```
sudo aptitude purge *insert-name-of-package-here*
sudo aptitude autoclean
```

---

### Post by Devin82m on 2010-06-26
lisati,

This is what I got when I tried:
```
sudo aptitude purge postfix
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  dictionaries-common{u} postfix{p} 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 4,309kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 
dpkg: warning: files list file for package `postfix' missing, assuming package has no files currently installed.
(Reading database ... 64524 files and directories currently installed.)
Removing postfix ...
invoke-rc.d: unknown initscript, /etc/init.d/postfix not found.
dpkg: error processing postfix (--purge):
 subprocess installed pre-removal script returned error exit status 100
Errors were encountered while processing:
 postfix
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done


This is what I got when I tried:
```
sudo aptitude autoclean
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Freed 0B of disk space


Then for the heck of it I tried this again:
```
sudo apt-get install -f
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  dictionaries-common{u} postfix{p} 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 4,309kB will be freed.
Do you want to continue? [Y/n/?] y
(Reading database ... 
dpkg: warning: files list file for package `postfix' missing, assuming package has no files currently installed.
(Reading database ... 64524 files and directories currently installed.)
Removing postfix ...
invoke-rc.d: unknown initscript, /etc/init.d/postfix not found.
dpkg: error processing postfix (--purge):
 subprocess installed pre-removal script returned error exit status 100
Errors were encountered while processing:
 postfix
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done


Thanks for the suggestions though! :D

---

### Post by kingolis on 2010-09-13
I was able to get around this by creating an empty file named postfix in the /etc/init.d directory.
```
sudo nano /etc/init.d/postfix
```

Save the file and re-run the
```
sudo aptitude purge postfix
sudo aptitude autoclean
```

At this point you can re-install postfix if you would like.

---

