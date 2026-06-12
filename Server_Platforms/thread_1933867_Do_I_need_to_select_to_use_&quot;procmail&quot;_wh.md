---
title: "Do I need to select to use &quot;procmail&quot; when re-configure the Postfix with Dovecot ?"
date: 2012-03-01
forum: Server Platforms
---

### Post by dchen on 2012-03-01
Hi all,

When I run "sudo dpkg-reconfigure postfix", do I need to say Yes to "Use Procmail for local delivery" ?   I'm not sure to answer yes or no AS I configure both Postfix and Dovecot servers.  If I do not use "procmail", does dovecot take care the local mail delivery or other default program will handle the local delivery ?  thx.

---

### Post by SeijiSensei on 2012-03-01
Agree to use [procmail]("http://man.flashnux.com/en/debian/6/6.0.1/man5/procmailrc.5.html").  You won't lose anything, and you'll gain access to an [extremely powerful]("http://man.flashnux.com/en/debian/6/6.0.1/man5/procmailex.5.html") "mail delivery agent" that might come in handy some day.

---

