---
title: "open files confguration does not change after trying all the the solutions provided."
date: 2016-03-03
forum: Server Platforms
---

### Post by satish8 on 2016-03-03
I know this post already exists but I have tried every possible solution provided in the forum to increase the open files in 

Distributor ID:    UbuntuDescription:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty


This is the change in the /etc/security/limits.conf


*       hard    nofile  100000        
*       soft    nofile  100000        
*       hard    nproc  100000        
*       soft    nproc  100000        
*       hard    core  100000
*       soft    core  100000

Similarly tried cat /etc/security/limits.d/60-nofile-limit.conf with same settings still no change.

Also tried /etc/pam.d/common-session settings with [COLOR=#666666][FONT=Consolas]session required pam_limits.so

[/FONT][/COLOR]Kindly help me resolve this issue let me know if you need any additional details to resolve this issue. I need this issue fixed in our production server. Help appreciated.

---

### Post by satish8 on 2016-03-03
When I ssh to the server and then type ulimit -a the open files in 1024. However, after sshing if I type su - username and then check the open files it displays the value from the limits.conf

---

