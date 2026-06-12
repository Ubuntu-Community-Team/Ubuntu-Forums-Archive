---
title: "Implementing repos server for Ubuntu/Centos/RedHat"
date: 2019-07-30
forum: Server Platforms
---

### Post by giobaxx on 2019-07-30
Hello guys

We are tryng to implement a repo server for both debian and Redhat Workstation in order to import locally the repositories we need. I have used the **apt-mirror** for the ubuntu repositories and is fine, and i'm trying to use **reposync** but i still have problems to understand how it works.
In general we would like to mirror not only the official repos from Canonical/RedHat but also some addition repos i.e webmin, Ros, ...and other in case of necessity

i've tried to mirror webadmin but i'm not able to do it

[PHP][Webmin] name=Webmin Distribution Neutral 
#baseurl=http://download.webmin.com/download/yum 
mirrorlist=http://download.webmin.com/download/yum/mirrorlist 
enabled=1[/PHP]

did you have some simple example where to start?

TAnks a lot

---

