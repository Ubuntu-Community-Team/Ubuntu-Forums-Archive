---
title: "Postfix - reconfigure mail directory to include domain name"
date: 2016-06-01
forum: Server Platforms
---

### Post by Icarusbop on 2016-06-01
Hello:
I am running a mail server with the MySQL, Postfix, Courier, SASL ( also with AMAVIS, Spamassasin, ClamAV, postfix admin & PHPmyadmin -  bit I don't think these are relevant to my query)
Postfix is configured to use virtual domains, aliaii and users, with a MySQL database. The database is the Postfixadmin database.
Everything is working fine.
The issue I have is users mailboxes are put straight into the (postfix) mail base folder with only their name for each mailbox. I now want to add a second domain to the system and therefore need to adjust my config so it puts different mailboxes into a sub-folder of the domain they belong to. I thought this would be quite easy but the solution has eluded me.
Here is (what I think) to be the relevant parts of postfix main.cf
```
    virtual_mailbox_base = /data/mail
    virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
```   
Here is the mysql_mailbox.cf file
```
    user=postfixadmin
    password=blahdyblah
    dbname=postfixadmin
    table=mailbox
    select_field=maildir
    where_field=username
    hosts=127.0.0.1
    additional_conditions = and active = 1
```
In the database, there are the following fields in the mailbox table (amongst others)
 - mailbox.home  # the base folder for the users mailbox
 - mailbox.maildir # the subfolder for the users mailbox
 - mailbox.username # username (the one they log in with, as opposed to just their name only)
 - mailbox.domain # The domain their mailbox belogs to
 
In the database the mailbox.home field currently contains the same string as the Postfix config 'virtual_mailbox_base' (i.e "/data/mail")
It seems that somewhere Postfix is configured to concatenate the two fields 'mailbox.home' and 'mailbox.maildir' (with a '/' in between) to create the mail location for the mailbox items, but I can't for the life on me figure out how to get it to include the 'mailbox.domain' field as well.
I'm sure it's quite simple when you know how, but I'm still learning.  Please can anyone advise?
I realise this only sorts out my mail delivery for Postfix, then I will need to deal with Courier IMAP to tell it to look in the correct location.
I think I have found where to do this:
file: /etc/courier/authmysqlrc
  ```
  MYSQL_MAILDIR_FIELD     concat(home,'/',maildir)
``` 
But first I need to get mail delivered to the right folder, then I can start looking at collecting it.
Thanks for any help.
Regards:
IcarusBop

---

### Post by howefield on 2016-06-01
Thread moved to the "*Server Platforms*" forum for a better fit.

---

