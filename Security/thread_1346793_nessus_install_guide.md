---
title: "nessus install guide"
date: 2009-12-05
forum: Security
---

### Post by yoma819 on 2009-12-05
now that nessus has been removed from the repositories can someone link an install guide for it?
tried just downloading the .deb from tenible security however it does not want to work!
cheers
yoma

---

### Post by Lars Noodén on 2009-12-06
Yes.  What you are looking for is now called OpenVAS:

[http://www.openvas.org/](http://www.openvas.org/)

---

### Post by Soul-Sing on 2009-12-06
1 install both the client and server (nessusd).

2 ```
sudo nessus-adduser Add a new nessusd user
```
-----------------------------------------------
Login : (create a login)
Authentication (pass/cert) [pass] : (do not put anything, just hit enter)

Login password : (create a password and don't forget it)
Login password (again) : (rinse, repeat)

User rules
---------------
nessusd has a rules system which allows you to restrict the hosts
that darknet has the right to test. For instance, you may want
him to be able to scan his own host only.

(please read the nessus-adduser man page for the rules syntax)

enter the rules for this user, and hit ctrl-D once you are done :
(the user can have an empty rules set)

(hit ctr-D here without entering any rules)

Login : thenameyougave
Password : ***********
DN :
Rules : Is that ok ? (y/n) [y] y
user added.

please note above, when you are asked about Authentication (pass/cert) [pass] just enter, as this is not needed for our install.
Also when you are asked about rules for the specific user, press CTRL+D because this is also beyond the scope of this tutorial and will not effect the install.

by default, nessusd has not started yet. to manully force him to, you will need to do the following:

3 ```
sudo /etc/init.d/nessusd start
```
nessus will work without being registered

registrating though gives you more, far more functionality

(source: world wide web :) )

---

