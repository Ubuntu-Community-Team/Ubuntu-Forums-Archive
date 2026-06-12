---
title: "Issue while updating my system."
date: 2018-02-20
forum: Ubuntu Development Version
---

### Post by arghayamondal123 on 2018-02-20
Hi guys,

I have installed Ubuntu 18.04 [ dev iso  ] on my system, everything is butter smooth. I am facing an issue when i update my system. 
Here is the error i am getting : [https://pastebin.com/S0LHuPJC](https://pastebin.com/S0LHuPJC)

---

### Post by wildmanne39 on 2018-02-20
*Thread moved to **Ubuntu Development Version, a more appropriate forum**.*

---

### Post by tinylagarto on 2018-02-20
You mean after doing an apt update followed by dist-upgrade?

---

### Post by mc4man on 2018-02-20
If still seeing after upgrading packages then post
```
apt-cache policy man-db
```
Sounds like this bug which was a while back & no longer an issue.
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=889608](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=889608)

---

### Post by arghayamondal123 on 2018-02-21
when  i do dist-upgrade i am getting this error.
i have even tried to update the mandb using following commands:
sudo mandb
sudo mandb --create

---

### Post by arghayamondal123 on 2018-02-21
Here is the output of following:
man-db:
  Installed: 2.8.1-1
  Candidate: 2.8.1-1
  Version table:
 *** 2.8.1-1 500
        500 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by vasa1 on 2018-02-21
> **arghayamondal123 said:**
> ... I am facing an issue **when i update my system**. ...
How are you updating your system?

Post the output of```
sudo apt-get update
```and then the output of```
sudo apt-get dist-upgrade
```if you can get that far.

---

### Post by arghayamondal123 on 2018-02-21
```
arghaya@grz361:~$ sudo apt update 
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Get:2 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease [4,487 B]                                                                                              
Get:3 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable/main amd64 Packages [2,261 B]                                                                                    
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                                                                                               
Hit:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease                                                                                        
Hit:6 [http://ppa.launchpad.net/jtaylor/keepass/ubuntu](http://ppa.launchpad.net/jtaylor/keepass/ubuntu) xenial InRelease                                                                                   
Hit:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                                                                    
Hit:8 [http://ppa.launchpad.net/serge-rider/dbeaver-ce/ubuntu](http://ppa.launchpad.net/serge-rider/dbeaver-ce/ubuntu) xenial InRelease                                                                      
Hit:9 [https://deb.opera.com/opera-stable](https://deb.opera.com/opera-stable) stable InRelease                                                                 
Get:10 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic InRelease [235 kB]                                                      
Hit:12 [http://ppa.launchpad.net/webupd8team/atom/ubuntu](http://ppa.launchpad.net/webupd8team/atom/ubuntu) bionic InRelease                                       
Hit:13 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic-updates InRelease                 
Hit:14 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Get:15 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic/main i386 Packages [1,008 kB]
Get:16 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages [1,012 kB]
Get:17 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic/main amd64 DEP-11 Metadata [444 kB]
Get:18 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [38.8 MB] 
Get:19 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic i386 Contents (deb) [38.5 MB]                                                                          
Get:20 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages [8,525 kB]                                                                     
Get:21 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic/universe i386 Packages [8,489 kB]                                                                      
Get:22 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic/universe Translation-en [4,941 kB]                                                                     
Get:23 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic/universe amd64 DEP-11 Metadata [2,970 kB]                                                              
Get:24 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic/multiverse amd64 DEP-11 Metadata [41.1 kB]                                                             
Fetched 70.6 MB in 5min 19s (221 kB/s)                                                                                                                   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
9 packages can be upgraded. Run 'apt list --upgradable' to see them.
```
gettin
I am getting the error i showed comes on doing dist-upgrade, though my packages are getting updated properly without any  issues, only getting that long list of error.

---

### Post by vasa1 on 2018-02-21
Was this a clean install? How do you have xenial ppas on your system?

---

### Post by tinylagarto on 2018-02-21
You are mixing repos. You have even PPAs for Xenial and Bionic. If you are on the development release of Bionic you should only have sources for Bionic in the list. 

Remove all entries with Xenial from your sources list. 

You should probably post your sources list:

```
cat /etc/apt/sources.list
```

---

### Post by arghayamondal123 on 2018-02-21
Yes it was a clean install.
Some ppa are not there for bionic so i managed to install the softwares using xenial repo.
May be xenial ppa are causing the issue.
Thanks for the support.

---

### Post by vasa1 on 2018-02-21
Well, please be careful with ppas! At this early stage, ppas for 18.04 may not be available. Even when they are, there could be instances where things may break badly.

To be able to recover from misadventure, have *ppa-purge*, *Synaptic Package Manager*, and *aptitude* installed. The last one can be really helpful in proposing ways to recover a broken system.

---

### Post by arghayamondal123 on 2018-02-21
sure thanks for the assist i have already installed the following packages, i know what ppa can do to my system.

---

### Post by Yellow Pasque on 2018-02-21
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=889608](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=889608)
Try this before updating and see if you still get errors:
```
export MAN_DISABLE_SECCOMP=1
```

If you're still having the issue after removing xenial packages and fully updating/upgrading your system, I think it's worth filing a bug report against man-db. This bug was supposedly fixed in man-db 2.8.1-1

---

### Post by arghayamondal123 on 2018-03-06
Hi, 

Latest update of man-db package fixed the issue.
 :D

---

