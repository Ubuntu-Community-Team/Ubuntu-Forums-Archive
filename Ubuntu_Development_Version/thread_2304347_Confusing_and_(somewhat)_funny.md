---
title: "Confusing and (somewhat) funny"
date: 2015-11-26
forum: Ubuntu Development Version
---

### Post by zika on 2015-11-26
```
:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following package was automatically installed and is no longer required:
  heirloom-mailx
Use 'apt-get autoremove' to remove it.
Done
The following NEW packages will be installed:
  s-nail
The following packages will be upgraded:
  heirloom-mailx
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 356 kB of archives.
After this operation, 261 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://archive.ubuntu.com/ubuntu/ devel/universe s-nail amd64 14.8.5-1 [352 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ devel/universe heirloom-mailx all 14.8.5-1 [4566 B]
Fetched 356 kB in 0s (1041 kB/s)          
Selecting previously unselected package s-nail.
(Reading database ... 312201 files and directories currently installed.)
Preparing to unpack .../s-nail_14.8.5-1_amd64.deb ...
Unpacking s-nail (14.8.5-1) ...
Preparing to unpack .../heirloom-mailx_14.8.5-1_all.deb ...
Unpacking heirloom-mailx (14.8.5-1) over (12.5-5) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Setting up s-nail (14.8.5-1) ...
Setting up heirloom-mailx (14.8.5-1) ...
Processing triggers for menu (2.1.47ubuntu1) ...
:~$ sudo apt-get autoremove 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  heirloom-mailx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 28,7 kB disk space will be freed.
Do you want to continue? [Y/n]n
```
Yes:> [COLOR=#333333][FONT=Ubuntu]heirloom-mailx: feature-rich BSD mail(1) -- transitional packagebut, still... ;)[/FONT][/COLOR]

---

