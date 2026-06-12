---
title: "Postfix new useradd can't authenticate others OK"
date: 2011-03-28
forum: Server Platforms
---

### Post by jeffk on 2011-03-28
This is a strange one: On an Ubuntu Server maverick 64-bit with postfix+ dovecot using normal passwd users, which has been working fine for ages, the most recent useradd isn't able to authenticate against postfix or dovecot, nor receive incoming internet mail. Mail from another local user is successfully delivered to this new user 'rsmith'.

Postfix and dovecot have been reloaded, then restarted, to no effect.

Here's a sanitized comparison of two users that work perfectly, the last one that doesn't.
```
$ sudo useradd -m -c R\ Smith -u 558 -g 100 -s /usr/sbin/nologin rsmith
$ sudo passwd rsmith

$ sudo grep smith /etc/passwd
jsmith:x:518:100:J Smith:/home/jsmith:/usr/sbin/nologin
rlsmith:x:557:100:R L Smith:/home/rlsmith:/usr/sbin/nologin
rsmith:x:558:100:R Smith:/home/rsmith:/usr/sbin/nologin
```
rsmith was added today, rlsmith a few months ago.

I suspect that postfix+dovecot aren't reading the passwd file like they normally do for whatever reason. Where is the regular local user map stored if not /etc/postfix? How do I force an update i.e. postmap like I would for /etc/postfix/virtuals, etc.?

Any information would be greatly appreciated.

---

### Post by elico on 2011-03-28
you must give us the mail log in order to see what is happening on the mail server.
> tail -f /var/log/mail.log

---

