---
title: "/etc/cron.daily/kolab-cyrus | bad mailbox in chkmbox fatal error: fatal error"
date: 2011-03-12
forum: Server Platforms
---

### Post by r6dude on 2011-03-12
Hello

I am pretty novice user of cyrus imap on linux(karmic) version 2.2.13-5build3.  Last night I started getting the error from /etc/cron.daily/kolab-cyrus cron task with the following error.

checking: user.jeff.Sent Messages (/var/spool/cyrus/mail/j/user/
jeff/Sent Messages)
 -> 11 records
bad mailbox user.jeff.Sent.invoice_contract in chkmbox
fatal error: fatal error

I checked the /var/spool/cyrus/mail/j/user/jeff/Sent path and invoice_contract folder doesn't exist.  I tried restoring from backup and still the same error.

Output of cyradm
localhost>lm *invoice_contract *
user/jeff/Sent/invoice_contract (\NonExistent \HasNoChildren)

Can somebody help please ?

Ajay

---

