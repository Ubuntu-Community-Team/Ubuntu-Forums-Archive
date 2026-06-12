---
title: "Dovecot + Maildir issues..?"
date: 2010-10-12
forum: Server Platforms
---

### Post by onemyndseye on 2010-10-12
Maybe I am misunderstanding something but according to this:

[http://wiki.dovecot.org/MailboxFormat/Maildir](http://wiki.dovecot.org/MailboxFormat/Maildir)


Unread emails are supposed to be contained in new/ ..  i.e: /home/myuser/Maildir/new/* 


Although on my system all mails are in cur/ even though they show up as unread in my client(s) (Kmail, Roundcube).  What gives?

The main problem comes in where I have written a bash wrapper for sa-learn to scan certain mail folders in every users maildir for HAM but this relies on the messages already being seen by the user.

*** Edit: 
  I forgot to add that my config consists of Dovecot + Postfix + amavis.  Postfix is configured to deliver mail via /usr/lib/dovecot/deliver

*** Solved:
Nothing to do with dovecot.  This is roundcube behavior.

---

