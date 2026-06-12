---
title: "Packages Cannot be Authenticated - Fresh Install of Feisty"
date: 2007-04-21
forum: Repositories &amp; Backports
---

### Post by chakkaradeep on 2007-04-21
Hi All,

I have Fresh Install of Feisty and tried to install some of gaim packages and i get that the packages cannot be authenticated. How to solve this ? Below is the output,

> 
chaks@chaks-laptop:~$ sudo apt-get install gaim-guifications
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gaim-guifications
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 167kB of archives.
After unpacking 1032kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  gaim-guifications
Install these packages without verification [y/N]? 
E: Some packages could not be authenticated


---

### Post by fwojciec on 2007-04-22
sudo apt-get update

---

### Post by mezhaka on 2007-12-09
indeed this helped thanks. do you know why is that?

---

