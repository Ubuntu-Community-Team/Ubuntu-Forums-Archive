---
title: "Install Apache Subversion 1.9.0 on Ubuntu server 14.04"
date: 2015-08-11
forum: Server Platforms
---

### Post by samuel38 on 2015-08-11
Hi, I try to install the new Apache Subversion 1.9.0 on my Ubuntu Server 14.04, that is actually running SVN 1.8.13. Actually I found nothing that helps me to install it on my server. Maybe I have to wait a littlebit to get a compiled Ubuntu package... But if anyone can help me with that, it will be appreciated.

---

### Post by Habitual on 2015-08-11
Describe how you attempted to install 1.9.0 please.
Any url references you read, used, went by...?

---

### Post by samuel38 on 2015-08-11
Thanks for your answer. First, I tried to update it with the same way I updated version 1.8.8 to version 1.8.13, (sudo apt-add-repository ppa:dominik-stadler/subversion-1.8). I tried replacing "1.8" by 1.9, but it don't works. I tried to install using WANdisco complied installation script for Ubuntu 14.04, but it don't seems to work (The sript was runned but the 1.8.13 version stay running). And, of course, I tried to download the version from apache subversion website, but this is not compiled and I don't know how I can compile this.

---

### Post by Habitual on 2015-08-11
Something wrong with 1.8.x?

---

### Post by samuel38 on 2015-08-11
No, there is no emergency to update the SVN version. But I would like to install the latest version to have all features and a maximum security if this is possible.

---

### Post by Habitual on 2015-08-11
Sorry, I won't help further. Nothing personal.
New users should stick to repo archives, IMO.

---

### Post by tibor-sekelj on 2016-03-29
> **Habitual said:**
> Sorry, I won't help further. Nothing personal.
New users should stick to repo archives, IMO.

What a jerk statement!

There is a serious bug in 1.8 in repo. Sometimes merges crash due to a well known bug from 1.8 which is fixed in 1.9.
14.04 is LTS and should provide possibility to upgrade to 1.9

Also this has nothing to do with 'New users'. Im on Ubuntu desktop since 2008 and do sysops on ubuntu servers. Still I would appreciate some help to upgrade to svn 1.9.

This solution has allowed me to upgrade to svn 1.9.x on 14.04
[http://tecadmin.net/install-subversion-1-9-on-ubuntu/](http://tecadmin.net/install-subversion-1-9-on-ubuntu/)

---

