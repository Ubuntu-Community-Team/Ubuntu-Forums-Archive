---
title: "Courier Mail Backup"
date: 2012-01-13
forum: Server Platforms
---

### Post by DanHorniblow on 2012-01-13
Hi, I am running a mail server with courier and postfix.

I want to regularly backup all email mailboxes within courier.

Any suggestions?

Cheers Dan

---

### Post by HermanAB on 2012-01-13
rsync of course.

---

### Post by DanHorniblow on 2012-01-14
> **HermanAB said:**
> rsync of course.

Don't I need another server to do that tho?

---

### Post by volkswagner on 2012-01-14
You can rsync to another machine, a separate folder, second hard drive, or to an external hard drive.

Perhaps you can add some specifics of what you would like to do and where the backups will reside.

---

### Post by DanHorniblow on 2012-01-14
Ok, Well I have bought a VPS and it is going to be hosting a number of websites plus email going to those domains.

I would like regular backups of "/var/vmail/" and "/var/www/" to be saved in to a compressed format and then maybe automatically FTP'd else where.

That would be my perfect solution in my mind. 


I would also like to backup MySQL databases what is the best method for that? 

Thanks Dan

---

