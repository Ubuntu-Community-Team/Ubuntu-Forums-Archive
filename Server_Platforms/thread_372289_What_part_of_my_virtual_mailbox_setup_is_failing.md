---
title: "What part of my virtual mailbox setup is failing?"
date: 2007-02-28
forum: Server Platforms
---

### Post by nibbo on 2007-02-28
Hi!
I have been trying to get a Virtual mailbox setup to work for some time now. I am using postfix together with dovecot. The setup is connected to a mysql-server administrated with postfixadmin. I have got squirrelmail (together with the provided config for dovecot) to work with the setup but i have problems when i try to connect with a email client.

When i connect with squirrelmail i get the following stuff in /var/log/mail.log
```
Feb 27 22:21:17 hades dovecot: auth-worker(default): mysql: Connected to localhost (postfix)
Feb 27 22:26:46 hades dovecot: auth(default): client in: AUTH^I1^IPLAIN^Iservice=IMAP^Isecured^Ilip=127.0.0.1^Irip=127.0.0.1^Iresp=<hidden>
Feb 27 22:26:46 hades dovecot: auth-worker(default): sql(box@nibbo.se,127.0.0.1): query: SELECT password FROM mailbox WHERE username = 'box@nibbo.se' AND active = '1'
Feb 27 22:26:46 hades dovecot: auth(default): client out: OK^I1^Iuser=box@nibbo.se
Feb 27 22:26:46 hades dovecot: auth(default): master in: REQUEST^I1^I24148^I1
Feb 27 22:26:46 hades dovecot: auth-worker(default): sql(box@nibbo.se,127.0.0.1): SELECT maildir, 5000 AS uid, 5000 AS gid FROM mailbox WHERE username = 'box@nibbo.se' AND active = '1'
Feb 27 22:26:46 hades dovecot: auth(default): master out: USER^I1^Ibox@nibbo.se^Imaildir=box@nibbo.se/^Iuid=5000^Igid=5000
Feb 27 22:26:46 hades dovecot: imap-login: Login: user=<box@nibbo.se>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Feb 27 22:26:46 hades dovecot: IMAP(box@nibbo.se): Disconnected: Logged out
Feb 27 22:26:46 hades dovecot: auth(default): client in: AUTH^I1^IPLAIN^Iservice=IMAP^Isecured^Ilip=127.0.0.1^Irip=127.0.0.1^Iresp=<hidden>
Feb 27 22:26:46 hades dovecot: auth-worker(default): sql(box@nibbo.se,127.0.0.1): query: SELECT password FROM mailbox WHERE username = 'box@nibbo.se' AND active = '1'
Feb 27 22:26:46 hades dovecot: auth(default): client out: OK^I1^Iuser=box@nibbo.se
Feb 27 22:26:46 hades dovecot: auth(default): master in: REQUEST^I2^I24147^I1
Feb 27 22:26:46 hades dovecot: auth-worker(default): sql(box@nibbo.se,127.0.0.1): SELECT maildir, 5000 AS uid, 5000 AS gid FROM mailbox WHERE username = 'box@nibbo.se' AND active = '1'
Feb 27 22:26:46 hades dovecot: auth(default): master out: USER^I2^Ibox@nibbo.se^Imaildir=box@nibbo.se/^Iuid=5000^Igid=5000
Feb 27 22:26:46 hades dovecot: imap-login: Login: user=<box@nibbo.se>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Feb 27 22:26:46 hades dovecot: IMAP(box@nibbo.se): Disconnected: Logged out
Feb 27 22:26:47 hades dovecot: auth(default): client in: AUTH^I1^IPLAIN^Iservice=IMAP^Isecured^Ilip=127.0.0.1^Irip=127.0.0.1^Iresp=<hidden>
Feb 27 22:26:47 hades dovecot: auth-worker(default): sql(box@nibbo.se,127.0.0.1): query: SELECT password FROM mailbox WHERE username = 'box@nibbo.se' AND active = '1'
Feb 27 22:26:47 hades dovecot: auth(default): client out: OK^I1^Iuser=box@nibbo.se
Feb 27 22:26:47 hades dovecot: auth(default): master in: REQUEST^I3^I24149^I1
Feb 27 22:26:47 hades dovecot: auth-worker(default): sql(box@nibbo.se,127.0.0.1): SELECT maildir, 5000 AS uid, 5000 AS gid FROM mailbox WHERE username = 'box@nibbo.se' AND active = '1'
Feb 27 22:26:47 hades dovecot: auth(default): master out: USER^I3^Ibox@nibbo.se^Imaildir=box@nibbo.se/^Iuid=5000^Igid=5000
Feb 27 22:26:47 hades dovecot: imap-login: Login: user=<box@nibbo.se>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Feb 27 22:26:47 hades dovecot: IMAP(box@nibbo.se): Disconnected: Logged out

```

and this is what fills my log when failing to connect with my email client:
```
Feb 28 07:04:00 hades dovecot: auth-worker(default): mysql: Connected to localhost (postfix)
Feb 28 07:04:20 hades dovecot: imap-login: Aborted login: rip=192.168.1.1, lip=192.168.1.60

```

Is there anyone that can see, by the looks of my logs, what part of my setup that is failing? Just tell me if i need to post more information.

---

### Post by Mr. C. on 2007-02-28
There are no log entries here indicating that postfix is being contacted.

Show the postfix syslog output.

---

