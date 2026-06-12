---
title: "HowTo Change Password direct on SquirrelMail Login Page"
date: 2007-12-09
forum: Server Platforms
---

### Post by satimis on 2007-12-09
Hi folks,


Ubuntu 7.04 server amd64
SquirrelMail


HowTo Change Password by users direct on the Login Page of SquirrelMail NOT via Usermin which I'm now doing.


I suppose it needs following package for my server.

Plugins 
Change password
[http://www.squirrelmail.org/plugins_category.php?category_id=5](http://www.squirrelmail.org/plugins_category.php?category_id=5)

Change_passwd
Details | Download 4.0
Original Author: Thiago Melo de Paula
This plugin is to allow your users to change his/her system password in
/etc/passwd or /etc/shadow 


I found follow on googling:-
HOWTO: Add a 'Change Password' button to SquirrelMail
[http://www.directadmin.com/forum/showthread.php?t=10532](http://www.directadmin.com/forum/showthread.php?t=10532)


very simple.  But I can't make it to work.  Now I have [Change
Password] button on the login page.    Clicking the button popup;```


Unable to connect

Firefox can't establish a connection to the server at domain.com:2222.

```


Port 2222 is open confirmed with ISP.  Their forum refused to help because I'm NOT running "DirAdmin".  Neither can I find a solution on Internet.


Now I want to try SquirrelMail's own plugin.  Please shed me some light.  TIA


B.R.
satimis

---

### Post by MJN on 2007-12-10
> **satimis said:**
> I suppose it needs following package for my server.

Plugins 
Change password
[http://www.squirrelmail.org/plugins_category.php?category_id=5](http://www.squirrelmail.org/plugins_category.php?category_id=5)

Change_passwd
Details | Download 4.0
Original Author: Thiago Melo de Paula
This plugin is to allow your users to change his/her system password in
/etc/passwd or /etc/shadow 


Those are two different plugins - 'Change Password' and 'Change_passwd' which use different methods for changing the user/system password. The latter plugin no longer works with the latest versions of SM - if you got to the SM users mailing list you can request a beta version of a new update.

The first plugin, 'change password', is inherently more secure (as it requires no root privileges to operate) however it does require you to run a poppass daemon.

> I found follow on googling:-
HOWTO: Add a 'Change Password' button to SquirrelMail
[http://www.directadmin.com/forum/showthread.php?t=10532](http://www.directadmin.com/forum/showthread.php?t=10532)


very simple.  But I can't make it to work. You'll have to ask the HowTo author as I am not familiar with it.

> Unable to connect

Firefox can't establish a connection to the server at domain.com:2222. 

Whilst your firewall is still running I will not attempt to diagnose the problem as your other posts suggest your firewall is currently doing more harm than good.

Mathew

---

### Post by satimis on 2007-12-10
> **MJN said:**
> Those are two different plugins - 'Change Password' and 'Change_passwd' which use different methods for changing the user/system password. The latter plugin no longer works with the latest versions of SM - if you got to the SM users mailing list you can request a beta version of a new update.

The first plugin, 'change password', is inherently more secure (as it requires no root privileges to operate) however it does require you to run a poppass daemon.

I'll follow the former 'Change Password' to see whether I can make it.


> 
You'll have to ask the HowTo author as I am not familiar with it.

The chance is remote.  They refuse to help because I'm NOT running DirAdmin.  Just posting it on the forum in anticipation some folks made it successfully.

I found a doc on howtoforge.com.  However the doc uses ISPConfig.  I'm running webmin.  Both are conflict each other.


satimis

---

