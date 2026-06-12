---
title: "Hello, i have problem with postfix after update to ubuntu 11.04"
date: 2011-10-19
forum: Server Platforms
---

### Post by uteliux on 2011-10-19
Hello, i have problem with postfix after update to ubuntu 11.04. Problem  starter just after update. I cant send email from email clients outlook  or thunderbird (error i got Relay access denied ) and asks for  passwords?? P.S. i can get new mail. But moust interesting that i can  send/recieve email thrue squirrelmail... in log files i see:

mail.log
Oct 17 19:43:02 **** postfix/smtpd[2256]: NOQUEUE: reject: RCPT from  hst-226-133.444us.lt[11.11.222.124]: 554 5.7.1 <****@gmail.com>:  Relay access denied; from=<arturas@*****.lt>  to=<****.lap@gmail.com> proto=ESMTP helo=<[192.168.1.104]>

this error i saw just after update in mail.err

Oct 17 16:03:22 ******** postfix/smtpd[30104]: fatal: no SASL authentication mechanisms
Oct 17 16:10:22 ******** postfix/smtp[22220]: fatal:  mysql:/etc/postfix/mysql-virtual_relaydomains.cf(0,lock|fold_fix): table  lookup problem
Oct 17 16:10:23 ******** postfix/error[22228]: fatal:  mysql:/etc/postfix/mysql-virtual_relaydomains.cf(0,lock|fold_fix): table  lookup problem
Oct 17 16:10:24 ******** postfix/qmgr[22216]: fatal:  mysql:/etc/postfix/mysql-virtual_relaydomains.cf(0,lock|fold_fix): table  lookup problem
Oct 17 17:05:09 ******** spamd[1328]: spamd: respawning server at /usr/sbin/spamd line 1140.

this is ubuntu perfect server with ispconfig 3 [http://www.howtoforge.com/perfect-se...at-ispconfig-3]("http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-3")

and already tried to reconfigure ispconfig 3 with update.php... please hellp

---

### Post by uteliux on 2011-10-19
Oct 19 10:52:42 ************** postfix/smtpd[19125]: warning:  karamele.************** .lt[************** .177]: SASL LOGIN  authentication failed: no mechanism available
Oct 19 10:52:43 **************  postfix/smtpd[19125]: disconnect from karamele.************** .lt[************** .177]

---

### Post by uteliux on 2011-10-19
from telnet i`m getting this error then trying to send email:
554 5.7.1 <artu****@gmail.com>: Relay access denied

---

### Post by smtp on 2011-10-20
I guess that you've got relay denied error because of problem with /etc/postfix/mysql-virtual_relaydomains.cf. It appears that postfix is not able to lookup there. Probably there is a password problem with that database (unfortunately I have zero exeirence with ISP config). You are abble to sendm mails via squirrelmail because these mails are sent from localhost which is enabled for relay. I would suggest to check access to mysql-virtual_relaydomains.cf via mysql tools.

---

### Post by uteliux on 2011-10-20
Hmm... i`ll try to check somehow... but i dont know how yet...

---

### Post by uteliux on 2011-10-21
smtp but after all, i can send mail from web mail client hosted on that server... and there are no mysql errors on mail.log.....

---

### Post by smtp on 2011-10-21
Sure, probably because localhost is allowed to relay via local postfix.

---

