---
title: "postfix/lmtp connection refused"
date: 2014-01-23
forum: Server Platforms
---

### Post by geloarcega on 2014-01-23
I'm new to ubuntu. I'm trying to configure postfix and dovecot with mySql as database.
I followed [https://library.linode.com]("https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql?format=print#sph_postfix").

I tried to send message using yahoo webmail to my email server.

here is the error from /var/log/mail.log

```
Jan 23 15:30:27 desktop-1 postfix/qmgr[7374]: CBF59A43293: from=<myUser@yahoo.com>, size=9304, nrcpt=1 (queue active)
Jan 23 15:30:27 desktop-1 postfix/lmtp[11153]: CBF59A43293: to=<user@domain.net>, relay=none, delay=13126, delays=13126/0.01/0/0, dsn=4.4.1, status=deferred (connect to desktop-1[private/dovecot-lmtp]: Connection refused)

```

can someone help me please? I'm new to ubuntu and this community. Thank you very much in advance. Ask information needed to help solve this. I don't know which are needed.

---

### Post by agarrett5 on 2014-04-01
I'm wondering if anyone has an answer to this?  

I have the same issue on Zimbra.  I am using Ubuntu Server 12.04 64-bit  LTS & Zimbra 8.0.6.GA.5922

Below is what is repeatedly in zimbra.log

> Apr  1 09:02:24 eserver postfix/lmtp[17609]: 43FC2C213F2: to=<system.report@<domain>>, relay=none, delay=588, delays=588/0.02/0/0, dsn=4.4.1, status=deferred (connect to <host.domain.com>[<ip address>]:7025: Connection refused)


One thing to note.  this is a email server I am setting up but isnt live yet.  It seems to be trying to connect to the live email server, which, incidentally, has same host name on same domain, which I think could be causing the receiving issues and the above error.  It is sending fine.

I have looked through both zimbra and ubuntu forums for the answer, this post was the closest to my question.

---

