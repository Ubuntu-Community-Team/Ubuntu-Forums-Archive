---
title: "Mail problem"
date: 2011-05-30
forum: Server Platforms
---

### Post by tapi0n on 2011-05-30
I'm setting up a postfix a postfix smtp server. When doing netcat everything comes back ok.

I'm using dovecot 2 as lmtp server. Which I'm sure is set up correctly (checked confs with a friend)

when doing */tail/var/log/mail.log* I get

```
May 30 19:50:31 gil postfix/smtpd[18368]: connect from wolk.domain.tld[xxx.xxx.xxx.xxx]
May 30 19:50:31 gil postfix/trivial-rewrite[18371]: warning: database /etc/postfix/virtual.db is older than source file /etc/postfix/virtual
May 30 19:50:31 gil postfix/cleanup[18372]: warning: database /etc/postfix/virtual.db is older than source file /etc/postfix/virtual
May 30 19:50:31 gil postfix/smtpd[18368]: 107652B0C4DA: client=wolk.domain.tld[xxx.xxx.xxx.xxx]
May 30 19:50:31 gil postfix/cleanup[18372]: 107652B0C4DA: message-id=<>
May 30 19:50:31 gil postfix/qmgr[18275]: 107652B0C4DA: from=<check@domain.tld>, size=302, nrcpt=1 (queue active)
May 30 19:50:31 gil postfix/smtpd[18368]: disconnect from wolk.domain.tld[xxx.xxx.xxx.xxx]
May 30 19:50:31 gil postfix/virtual[18373]: warning: maildir access problem for UID/GID=5000/5000: create maildir file /var/vmail/user1/tmp/1306777831.P18373.gil: Permission denied
May 30 19:50:31 gil postfix/virtual[18373]: warning: perhaps you need to create the maildirs in advance
May 30 19:50:31 gil postfix/virtual[18373]: 107652B0C4DA: to=<user1@sub.domain.tld>, relay=virtual, delay=0.02, delays=0.01/0/0/0, dsn=4.2.0, status=deferred (maildir delivery failed: create maildir file /var/vmail/user1/tmp/1306777831.P18373.gil: Permission denied)

```when running *tail /var/log/dovecot.log *I get this for output
```
2011-05-30 19:50:31 auth(default): Info: client out: OK    1    user=user1@sub.domain.tld
2011-05-30 19:50:31 auth(default): Info: master in: REQUEST    139    18340    1
2011-05-30 19:50:31 auth(default): Info: passwd(user1@sub.domain.tld,xxx.xxx.xxx.xxx): lookup
2011-05-30 19:50:31 auth(default): Info: passwd(user1@sub.domain.tld,xxx.xxx.xxx.xxx): unknown user
2011-05-30 19:50:31 auth(default): Info: passwd-file(user1@sub.domain.tld,xxx.xxx.xxx.xxx): lookup: user=user1@sub.domain.tld file=/etc/dovecot/passwddov
2011-05-30 19:50:31 auth(default): Info: master out: USER    139    user1@sub.domain.tld   uid=5000    gid=5000    home=/var/vmail/user1    mail=maildir:/var/vmail/user1
2011-05-30 19:50:31 imap-login: Info: Login: user=<user1@sub.domain.tld>, method=PLAIN, rip=xxx.xxx.xxx.xxx, lip=xxx.xxx.xxx.xxx, TLS
2011-05-30 19:50:31 IMAP(user1@sub.domain.tld): Error: mkdir(/var/vmail/user1/cur) failed: Permission denied (euid=5000(<unknown>) egid=5000(<unknown>) missing +w perm: /var/vmail/user1)
2011-05-30 19:50:31 IMAP(user1@sub.domain.tld): Info: Connection closed bytes=20/400
2011-05-30 19:50:31 auth(default): Info: new auth connection: pid=18376

```Could someone please help me? This is driving me mental. I have no idea what I'm doing wrong and need to get this sorted out.


Edit: there was a problem with permissions, all fixed now.

---

