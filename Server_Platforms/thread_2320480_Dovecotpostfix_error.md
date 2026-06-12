---
title: "Dovecot/postfix error"
date: 2016-04-14
forum: Server Platforms
---

### Post by Timobrunn on 2016-04-14
Hello,

i'm not able to send or recieve emails

the log:
```
Apr 14 12:45:08 Braver-Scanlation dovecot: imap-login: Login: user=<admin@braver-sl.esy.es>, method=PLAIN, rip=::1, lip=::1, mpid=1362, secured, session=<oy/9nXQwsQAAAAAAAAAAAAAAAAAAAAAB>Apr 14 12:45:08 Braver-Scanlation dovecot: imap(admin@braver-sl.esy.es): Disconnected: Logged out in=44 out=460
Apr 14 12:45:36 Braver-Scanlation postfix/smtpd[1365]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Apr 14 12:45:36 Braver-Scanlation postfix/smtpd[1365]: connect from localhost[::1]
Apr 14 12:45:36 Braver-Scanlation postfix/smtpd[1365]: 9C9123022D5: client=localhost[::1]
Apr 14 12:45:36 Braver-Scanlation postfix/cleanup[1368]: 9C9123022D5: message-id=<abbda9f18e3e2eb99f1be5e63d364caf@braver-sl.esy.es>
Apr 14 12:45:36 Braver-Scanlation postfix/qmgr[1092]: 9C9123022D5: from=<admin@braver-sl.esy.es>, size=255, nrcpt=1 (queue active)
Apr 14 12:45:36 Braver-Scanlation dovecot: imap-login: Login: user=<admin@braver-sl.esy.es>, method=PLAIN, rip=::1, lip=::1, mpid=1372, secured, session=<r1+rn3QwtwAAAAAAAAAAAAAAAAAAAAAB>
Apr 14 12:45:36 Braver-Scanlation postfix/error[1369]: 9C9123022D5: to=<******1@gmail.com>, relay=none, delay=0.31, delays=0.28/0.01/0/0.02, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]:10024: Connection refused)
Apr 14 12:45:36 Braver-Scanlation postfix/smtpd[1365]: disconnect from localhost[::1]
Apr 14 12:45:36 Braver-Scanlation dovecot: imap(admin@braver-sl.esy.es): Disconnected: Logged out in=380 out=569
Apr 14 12:45:37 Braver-Scanlation dovecot: imap-login: Login: user=<admin@braver-sl.esy.es>, method=PLAIN, rip=::1, lip=::1, mpid=1375, secured, session=<z/K0n3QwwgAAAAAAAAAAAAAAAAAAAAAB>
Apr 14 12:45:37 Braver-Scanlation dovecot: imap(admin@braver-sl.esy.es): Disconnected: Logged out in=44 out=460
Apr 14 12:45:37 Braver-Scanlation dovecot: imap-login: Login: user=<admin@braver-sl.esy.es>, method=PLAIN, rip=::1, lip=::1, mpid=1378, secured, session=</Ee6n3QwxAAAAAAAAAAAAAAAAAAAAAAB>
Apr 14 12:45:37 Braver-Scanlation dovecot: imap(admin@braver-sl.esy.es): Disconnected: Logged out in=290 out=1347
Apr 14 12:45:37 Braver-Scanlation dovecot: imap-login: Login: user=<admin@braver-sl.esy.es>, method=PLAIN, rip=::1, lip=::1, mpid=1380, secured, session=<bVO7n3QwxQAAAAAAAAAAAAAAAAAAAAAB>
Apr 14 12:45:37 Braver-Scanlation dovecot: imap(admin@braver-sl.esy.es): Disconnected: Logged out in=82 out=526



```

Does somebody know why i can't send or recieve emails?

Im using:
Roundcube
Postfix
Postfixadmin
MySQL
Ubuntu 15.04 Vivet

---

