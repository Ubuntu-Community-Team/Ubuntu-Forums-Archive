---
title: "sendmail problem"
date: 2008-07-08
forum: Server Platforms
---

### Post by nebben11 on 2008-07-08
Hello all!
Heres the problem I'm having:
I'm using no-ip.com's dns stuff for my server and I'm trying to get logwatch to send the log to my email on gmail account. Well in testing sendmail Local emails work great but I cant receive any emails from remote email address's 
can some one please help me on this problem 
Thanks, Ben

---

### Post by windependence on 2008-07-09
Well you should probably install Postfix which is a drop in replacement for sendmail so don't remove sendmail, just apt-get install postfix and you should be fine. To receive e-mail you will need something like Dovecot or Courier-Imap. 

-Tim

---

### Post by nebben11 on 2008-07-09
apt-get wants to remove sendmail and sendmail-bin

---

### Post by cjacobsen on 2009-01-21
Install postfix with a Gmail relay. It's pretty simple. Click on cjacobsen.net in my signature and go to the preface in ubuntu security howto.

---

