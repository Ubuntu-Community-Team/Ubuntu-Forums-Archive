---
title: "Advise for migrating IMAP to new Citadel server"
date: 2009-12-12
forum: Server Platforms
---

### Post by volkswagner on 2009-12-12
I am in the process of migrating and email server.  My current server is configured using Posfix/Courrier-IMAP.

There are only a few users over a couple domains.  Clients have been using Evolution Mail and Outlook Express.

I have not been able to locate info on saving the old mail either locally with each client, or how to transfer IMAP folders to the new Citadel server.


From what I have read, the Citadel server stores the mail in a DataBase.

---

### Post by volkswagner on 2010-01-01
I am surprised no comments here.  

If anyone finds this thread looking for help, I have been pointed to[ Citadel site]("http://www.citadel.org/doku.php/faq:favoriteclient:migrating_mail_into_citadel#how.do.i.move.all.of.my.mail.from.a.legacy.mail.server.to.citadel").

I used the [imapcopy.pl]("http://www.athensfbc.com/imap_tools/files/imapcopy.pl") script directly, which is part of [IMAP Tools]("http://www.athensfbc.com/imap_tools/").....works a treat.  

One thing to note:  My Postfix/Courrier-IMAP setup listed "sent" as the directory and Citadel list "sent items" as the directory.  When the copy was finished, I ended up with a new folder "sent" with the contents.  This was fine for me, acting as an archive.  I am sure mods would have forced the merge of "sent" and "sent items" folders.  I just did not have the need.

---

