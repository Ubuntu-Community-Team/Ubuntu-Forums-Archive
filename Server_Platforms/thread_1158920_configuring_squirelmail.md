---
title: "configuring squirelmail"
date: 2009-05-14
forum: Server Platforms
---

### Post by pawan_lal on 2009-05-14
hi all,
i had configured postfix in my office n its running sommoth, now i want to access my postfix outside lan also for that i have to do ssl port forwarding in my router that ill do.now can ne 1 plz guide me in configuring squireelmail so that i can access postfix from outside.my os is - ubuntu 8.04 LTS
thx

---

### Post by a9k3d on 2009-05-14
Squirelmail gives web-based mailbox access. It needs to access your email via IMAP. Postfix provides SMTP (outbound email). You will need an IMAP server - dovecot is good. Postfix and Dovecot will have to be set to both use the same style of storing emails (mbox, maildir etc)
Once your IMAP and SMTP servers are running, setting up squirrelmail is easy - you run config/conf.pl

See the [Squirrelmail configuration]("http://squirrelmail.org/docs/admin/admin-5.html") page

---

