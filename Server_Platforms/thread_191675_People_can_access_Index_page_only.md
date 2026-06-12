---
title: "People can access Index page only"
date: 2006-06-07
forum: Server Platforms
---

### Post by skafiskafnjak on 2006-06-07
I installed InvisionPowerBoard on Ubuntu Linux LAMP server 6.06. 

Me as a local user can access all pages and forum is working nice but all other people from the internet can access Index page only. 
If they try to access any other forum they get message "page can not be displayed"

What is the problem?

I set for 192.168.0.myIP that port 80 is open.

---

### Post by adamkane on 2006-06-09
This probably has to do with your permissions for the directory /var/www. You need to allow access to the user/group apache/apache. This is a VERY common issue, so you should be able to find specific help on the InvisionPowerBoard forum.

---

