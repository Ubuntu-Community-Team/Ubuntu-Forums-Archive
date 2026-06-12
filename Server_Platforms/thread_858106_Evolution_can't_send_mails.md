---
title: "Evolution can't send mails"
date: 2008-07-13
forum: Server Platforms
---

### Post by satimis on 2008-07-13
Hi folks,


Remote Server
Ubuntu LAMP 6.06 amd64
postfix
cyrus


Evolution can receive mails on remote server but can't send mails via it with same password.


$ tail /var/log/mail.log```

Jul 13 19:06:52 satimis postfix/smtpd[4511]: connect from unknown[220.232.213.178]
Jul 13 19:07:06 satimis postfix/smtpd[4511]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such 
file or directory
Jul 13 19:07:06 satimis postfix/smtpd[4511]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such 
file or directory
Jul 13 19:07:06 satimis postfix/smtpd[4511]: warning: SASL authentication failure: Password verification failed
Jul 13 19:07:06 satimis postfix/smtpd[4511]: warning: unknown[220.232.213.178]: SASL PLAIN authentication failed
Jul 13 19:07:15 satimis postfix/smtpd[4511]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such 
file or directory
Jul 13 19:07:15 satimis last message repeated 3 times
Jul 13 19:07:15 satimis postfix/smtpd[4511]: warning: SASL authentication failure: Password verification failed
Jul 13 19:07:15 satimis postfix/smtpd[4511]: warning: unknown[220.232.213.178]: SASL PLAIN authentication failed
Jul 13 19:07:19 satimis postfix/smtpd[4511]: disconnect from unknown[220.232.213.178]

```


$ sudo ls /etc | grep sasldb2```

sasldb2

```


$ ls -l /etc/sasldb2```

-rw-rw---- 1 root sasl 12288 2008-06-15 15:20 /etc/sasldb2

```


$ cat /etc/group | grep postfix```

mail:x:8:dovecot,postfix,cyrus
postfix:x:111:

```


Can I enter "sasl"

on;```

mail:x:8:dovecot,postfix,cyrus,sasl

```


OR on;```

postfix:x:111:sasl

```

to solve the problem?  TIA


B.R.
satimis

---

### Post by skunkbad on 2008-07-13
In your /etc/postfix/main.cf, is 220.232.213.178 listed in mynetworks?

---

### Post by satimis on 2008-07-14
> **skunkbad said:**
> In your /etc/postfix/main.cf, is 220.232.213.178 listed in mynetworks?
Hi skunkbad,


No.

$ grep mynetworks /etc/postfix/main.cf ```

mynetworks = 127.0.0.0/8
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination

```

Performed following test

adding 220.232.213.178 to mynetworks
```

mynetworks = 127.0.0.0/8, 220.232.213.178

```

$ sudo /etc/init.d/postfix restart


Started Evolution.

Send mail still failure.


Edit-1:

To my surprise I can send and receive email on SquirrelMail with the same password via remote server.


Edit-2:

After ssh connect the remote server on Xterm, local PC.  I can telnet localhost 25 to send a mail to yahoo without problem.


What obstruction makes the user unable to authenticate?


B.R.
satimis

---

