---
title: "Ubuntu Server Mail"
date: 2011-01-10
forum: Server Platforms
---

### Post by Mike9182 on 2011-01-10
How much resources are needed to run a mail server with approximately 75 boxes?

---

### Post by SeijiSensei on 2011-01-10
Not much unless you're also scanning each message for viruses and spam. Then more memory and more CPU are always worthwhile.  It also depends on how vulnerable your users' accounts are to spammers.  I have some mailboxes that receive literally hundreds of spam messages a day.  I have two layers of defense in place, but still my scanning and delivery box (running MailScanner with SpamAssassin and ClamAV) can have some pretty high loads midday. 

If you're just accepting mail with an MTA like Postfix or sendmail and delivering it to mailboxes that are accessed via a POP/IMAP server like dovecot, you could easily handle this using an old PC with 512MB of memory and a P4.

---

### Post by elico on 2011-01-10
a small machine will do for it.
basic desktop will do most of the job
and if you want somethig ready you can download TURNKEY LINUX APPLIANCE 


[http://www.turnkeylinux.org/zimbra](http://www.turnkeylinux.org/zimbra)

---

