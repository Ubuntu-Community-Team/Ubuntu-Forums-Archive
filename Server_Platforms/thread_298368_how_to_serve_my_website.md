---
title: "how to serve my website ?"
date: 2006-11-12
forum: Server Platforms
---

### Post by eilker1917 on 2006-11-12
firstly sorry for newbie questions...

1/ what is the difference between ubuntu and ubuntu-server ?  is the difference only lamp server ? 

2/ i have already installed kubuntu 6.06 to my pc, and also installed lamp server myself (not from cd)

myquestion: i have a simple web site in  /var/www folder. what must i do to serve mysite. i wanna learn this, how can myfriends see my simple website ? i give my ip, they directly see my modem settings login screen.

is it releated dydns thing etc ?

thanx for any help...

note: i know that being a host is not good for pc, i ask only for learning...
note2: i connect to internet by router...

---

### Post by DaveBorealis on 2006-11-12
> **eilker1917 said:**
> what is the difference between ubuntu and ubuntu-server ?  is the difference only lamp server ? 

The server is installed with no GUI, such as Gnome or KDE desktops.  It also has the various server software installed, such as Apache.

> i have a simple web site in  /var/www folder. what must i do to serve mysite.

You'll have to do port forwarding with your router, sending port 80 requests to your computer and apache.

Hope this gets you started,
Dave

---

### Post by eilker1917 on 2006-11-12
> **DaveBorealis said:**
> The server is installed with no GUI, such as Gnome or KDE desktops.  It also has the various server software installed, such as Apache.



You'll have to do port forwarding with your router, sending port 80 requests to your computer and apache.

Hope this gets you started,
Dave

thank you, now i serve my website:)

---

