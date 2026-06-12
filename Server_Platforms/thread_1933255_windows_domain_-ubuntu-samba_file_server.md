---
title: "windows domain -ubuntu-samba file server"
date: 2012-02-28
forum: Server Platforms
---

### Post by tchandu17 on 2012-02-28
Hi,
 
I want to use cross platform for my organiation.. i am using Windows active directory as my domain controller. and i would like to use ubuntu-samba as file server..
 
My main goal is to make use of windows active directory users and groups for all the folders and files.. 
 
i.e 
 
if i assign any permission to any windows users through samba .. it should work.. and alos i want to know how can i integare windows and ubuntu.

---

### Post by zeljkojagust on 2012-02-29
In short, you need winbind service and you need to map windows users and groups on your linux samba server. It's not something it can be done in an hour or two, it's a lot of work. The best thing you can do for starters is consult with samba documentation, parts related to Windows integration. And I would not do this on a live environment before I test everything.

---

