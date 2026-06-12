---
title: "Getting rid of SQL+Tomcat"
date: 2009-02-25
forum: Server Platforms
---

### Post by ooobooontooo on 2009-02-25
Hi,

I recently had to install SQL and Tomcat for a recent project. Can someone provide me with tips to COMPLETELY get rid of SQL and Tomcat? (I no longer need them and feel that they would just take up space...) My approach right now is to purge SQL and Tomcat and run autoremove...But I think I tried purging it last time, and there were still some databases left behind and stuff... Thanks in advan.ce

---

### Post by ooobooontooo on 2009-03-05
Any advice?

---

### Post by ooobooontooo on 2009-03-17
bump

---

### Post by Vegan on 2009-03-17
yawn......

sudo apt-get remove tomcat
sudo apt-get remove mysql

or whatever the database you are using is.

---

### Post by ooobooontooo on 2009-03-17
> yawn......

sudo apt-get remove tomcat
sudo apt-get remove mysql

or whatever the database you are using is.

Firstly, I want to COMPLETELY remove these things, so it should be "purge". Second, I don't think that gets rid of things like SQL root password and such, so I'm thinking there are still some config files that are not touched by apt-get. I'm asking how can I surely get rid of these things (like the SQL root password)?

---

### Post by ooobooontooo on 2009-03-24
Sorry to drag this on...but help?

---

