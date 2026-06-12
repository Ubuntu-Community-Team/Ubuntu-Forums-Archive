---
title: "Invalid Installation of Bacula Administration Tool"
date: 2009-10-20
forum: Server Platforms
---

### Post by yokey on 2009-10-20
I just installed "Bacula Administration Tool" and tried to start it. I get the message:

> /usr/sbin/bat (No such file or directory)

I noticed that the executeable is located */usr/bin/bat* but changing the menu entry still does not solve the problem as the program tries to read */etc/bacula/bat.conf* which is owned by root:bacula and has no global read access. 

I hope i was not wrong posting this here.

---

### Post by felcore5 on 2009-10-20
Hi Yokey,

Go to a terminal and cd to /etc/bacula
Run the util by typeing sudo bat
This should start the app for you.

It does not run properly from the menu because it does not ask to admin password.


> **yokey said:**
> I just installed "Bacula Administration Tool" and tried to start it. I get the message:



I noticed that the executeable is located */usr/bin/bat* but changing the menu entry still does not solve the problem as the program tries to read */etc/bacula/bat.conf* which is owned by root:bacula and has no global read access. 

I hope i was not wrong posting this here.

---

### Post by yokey on 2009-10-21
> **felcore5 said:**
> 
Run the util by typeing sudo bat


Of course this works for me. And i start it this way. I also found the bug is already [fixed for karmic]("https://bugs.launchpad.net/ubuntu/+source/bacula/+bug/445284").

---

