---
title: "Mail Server with virtual users (permission denied)"
date: 2012-09-14
forum: Server Platforms
---

### Post by Do$ on 2012-09-14
Dear Sirs.
I've tried to install mail server for my ubuntu.
I've used the following article: [http://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/](http://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/)
All is working except, that while sending messages, postfix can't deliver my message to local mailbox:
I have such error:
dovecot: lda: Error: userdb lookup: connect(/var/run/dovecot/auth-userdb) failed: Permission denied (euid=150(vmail) egid=8$

I'm using virtual users and I can't understand, why I have such problem.

Please advice.
Tx.

---

