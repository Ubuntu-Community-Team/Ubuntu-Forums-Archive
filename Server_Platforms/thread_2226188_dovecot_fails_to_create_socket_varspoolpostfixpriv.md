---
title: "dovecot fails to create socket /var/spool/postfix/private/auth"
date: 2014-05-25
forum: Server Platforms
---

### Post by lister171254 on 2014-05-25
After following this link [http://wiki2.dovecot.org/HowTo/PostfixAndDovecotSASL](http://wiki2.dovecot.org/HowTo/PostfixAndDovecotSASL) to configure devecot with postfix I've found the problem that dovecot does not create the socket "/var/spool/postfix/private/auth" at startup.

There are no errors in any of the logs as to the cause of this, so am somewhat stumped as to how this can be resolved

Thanks

---

### Post by danieljsamson on 2014-05-27
I followed the ubuntu server guide and it am having the similar problem.
 
try:
[https://help.ubuntu.com/14.04/serverguide/postfix.html#postfix-troubleshooting](https://help.ubuntu.com/14.04/serverguide/postfix.html#postfix-troubleshooting)

You should run "tail -f /var/log/mail.err"  This will tell you why it is not working. 

When i run it i get this message  postfix/smtpd[20866]: fatal: no SASL authentication mechanisms.

i think /etc/dovecot/conf.d/10-master.cf holds the key to the configuration. But when I run "service dovecot status"
i get "stopped/waiting" and there is no dovecot file in /etc/init.d/.

I hope this helps?

---

### Post by lister171254 on 2014-05-29
The problem was that the following line was missing from my dovecot.conf 

!include conf.d/*.conf

I found this by invoking the following

dovecot -n

which shows the non default setting

---

