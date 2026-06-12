---
title: "Ubuntu 14.04 Server install"
date: 2018-12-07
forum: Server Platforms
---

### Post by bd5pilot on 2018-12-07
Hi all!
Anybody can help in some strange bug, 
I just tried to reinstall ubuntu server (14 version) created by recipe "The perfect server" 

[https://www.howtoforge.com/tutorial/ubuntu-perfect-server-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/](https://www.howtoforge.com/tutorial/ubuntu-perfect-server-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/)

There link to Ubuntu 17. version, but 18 bugged the same way. 
The smtp login from mail client do not successful. 


root@edge:/var/log# tail mail.log
Dec  7 20:49:34 edge postfix/smtpd[20349]: disconnect from localhost[::1] ehlo=1 mail=1 rcpt=0/1 rset=1 quit=1 commands=4/5
Dec  7 20:50:02 edge postfix/smtpd[20349]: connect from localhost[::1]
Dec  7 20:50:02 edge postfix/smtpd[20349]: lost connection after CONNECT from localhost[::1]
Dec  7 20:50:02 edge postfix/smtpd[20349]: disconnect from localhost[::1] commands=0/0
Dec  7 20:50:02 edge dovecot: pop3-login: Disconnected (no auth attempts in 0 secs): user=<>, rip=::1, lip=::1, secured, session=<RxYwFXN8UOQAAAAAAAAAAAAAAAAAAAAB>
Dec  7 20:50:02 edge dovecot: imap-login: Disconnected (disconnected before auth was ready, waited 0 secs): user=<>, rip=::1, lip=::1, secured, session=<qBcwFXN8KqgAAAAAAAAAAAAAAAAAAAAB>
Dec  7 20:53:17 edge dovecot: anvil: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Dec  7 20:53:17 edge dovecot: log: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Dec  7 20:53:17 edge dovecot: master: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Dec  7 20:53:17 edge dovecot: master: Dovecot v2.2.27 (c0f36b0) starting up for imap, pop3 (core dumps disabled)
root@edge:/var/log# tail mail.log
Dec  7 20:53:17 edge dovecot: log: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Dec  7 20:53:17 edge dovecot: master: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Dec  7 20:53:17 edge dovecot: master: Dovecot v2.2.27 (c0f36b0) starting up for imap, pop3 (core dumps disabled)
Dec  7 20:54:55 edge dovecot: pop3-login: Login: user=<747@robaero.com>, method=PLAIN, rip=83.99.234.227, lip=192.168.0.100, mpid=20569, TLS, session=<N/eqJnN87MxTY+rj>
Dec  7 20:54:55 edge dovecot: pop3(747@robaero.com): Disconnected: Logged out top=0/0, retr=0/0, del=0/1, size=1062
Dec  7 20:55:02 edge dovecot: pop3-login: Disconnected (no auth attempts in 0 secs): user=<>, rip=::1, lip=::1, secured, session=<DOAUJ3N8XOQAAAAAAAAAAAAAAAAAAAAB>
Dec  7 20:55:02 edge dovecot: imap-login: Disconnected (no auth attempts in 0 secs): user=<>, rip=::1, lip=::1, secured, session=<1OEUJ3N8NqgAAAAAAAAAAAAAAAAAAAAB>
Dec  7 20:55:02 edge postfix/smtpd[20639]: connect from localhost[::1]
Dec  7 20:55:02 edge postfix/smtpd[20639]: lost connection after CONNECT from localhost[::1]
Dec  7 20:55:02 edge postfix/smtpd[20639]: disconnect from localhost[::1] commands=0/0

here are fragment from mail.log

Anybody have solution for situation?

Hope for help,
Serge.

---

### Post by howefield on 2018-12-07
Thread moved to its own thread and to the "*Server Platforms*" forum.

---

