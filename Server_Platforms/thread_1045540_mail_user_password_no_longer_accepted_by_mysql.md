---
title: "mail user password no longer accepted by mysql"
date: 2009-01-20
forum: Server Platforms
---

### Post by volkswagner on 2009-01-20
My mail server is down /postfix/courier-imap/mysqlauth.

A friend notified me mail sent to me, by him, was bounced back as undeliverable.

Postfix is running, so is mysql and courier.  According to the logs the password for user=mail is no longer accepted by mysql.

In the mysql_mailbox.cf, the password is cryptic.  I cant' remember if it should be clear text or not.

How could this happen?  I did recently have a near lockup due to overload of resources.  I also recently installed Jinzora.

I don't want to just change the password without a better understanding of what happened.

TIA

EDIT: Well after double checking the password for all $.cf files, it is clear text and the password I set.

What other services may need to be restarted?  I tried, Mysql, Postfix, courier-imap, courier-authdaemon.

---

### Post by volkswagner on 2009-01-20
Going down for a reboot.  Fingers are crossed!

---

### Post by volkswagner on 2009-01-20
I like to live dangerously.  I even ran a full update/upgrade before reboot.

All is well after reboot.

Just another reason to upgrade my hardware.  This all stemmed from overloading the machine.  I broke something when trying to upload a .tar.gz file nearly as large as physical Ram.

---

