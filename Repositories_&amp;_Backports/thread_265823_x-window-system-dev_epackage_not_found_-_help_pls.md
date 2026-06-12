---
title: "x-window-system-dev e:package not found - help pls"
date: 2006-09-26
forum: Repositories &amp; Backports
---

### Post by mesh on 2006-09-26
Trying to install mplayer using this guide [http://ubuntuforums.org/showthread.php?t=31061](http://ubuntuforums.org/showthread.php?t=31061) 


I got to the part where im supose to install x-window-system-dev, but the package wasnt found. Below is my sources.list file. Anyone have any idea why i cant find it. I tried seraching and listed all my installed packages and its not installed and i cannot find it. I could only find x-window-system-core, but thats already installed.


## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by amohanty on 2006-09-26
Just a thought - but why dont you try to install mplayer from the repos?

Any specific reason why you want to install from source??

AM

---

### Post by mesh on 2006-09-26
Because im a noob :D. Ill be sure and try that next. Thanks for taking the time. Peace


UPDATE: that was easy. :D.Thx again.

---

