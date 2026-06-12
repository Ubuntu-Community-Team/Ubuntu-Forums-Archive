---
title: "how do i set message_size_limit in postfix"
date: 2007-10-17
forum: Server Platforms
---

### Post by demiurgen on 2007-10-17
i find the main.cf file inside /etc/postfix, open it up and search for :
message_size_limit

phrase not found... its not there...??


where can i find it if its not in main.cf?


i have set up my mail server following this guide:
[http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy)

---

### Post by foxylad on 2007-10-17
It's not there because you haven't put it in there. Postfix (and most linux applications) will use default settings if entries don't exist. 

Try adding it and then running **postconf -d** - this will tell you waht all settings are.

---

### Post by MJN on 2007-10-18
(Sorry foxylad - I seem to be following you around here!)

Note that **postconf -d** will list the default values of all settings so if you've added a particular directive this won't be reflected in the list (postconf -n will however show this, if it's been set).

Mathew

---

