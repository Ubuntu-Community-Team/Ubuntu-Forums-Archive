---
title: "disadvantage of file based email server"
date: 2011-03-02
forum: Server Platforms
---

### Post by ishk on 2011-03-02
hi
just wanted to know what are the disadvantage of file based email server. why cant we use database as a mail storage? i googled but i couldn't found any answers for this
thanks

---

### Post by HermanAB on 2011-03-03
Howdy,

Citadel uses a database backend for everything.  
[http://citadel.org](http://citadel.org)

The obvious advantage is that if HR sends the same 10MB attachment to 20,000 employees, then the Citadel mail server will only save one copy, while with a Postfix based system, you will need to run out to buy more disk drives for the mail server.

---

### Post by mciverza on 2011-03-03
> **HermanAB said:**
> Howdy,

Citadel uses a database backend for everything.  
[http://citadel.org](http://citadel.org)

The obvious advantage is that if HR sends the same 10MB attachment to 20,000 employees, then the Citadel mail server will only save one copy, while with a Postfix based system, you will need to run out to buy more disk drives for the mail server.

Zimbra does that too: [http://www.zimbra.com](http://www.zimbra.com)

---

### Post by SeijiSensei on 2011-03-03
Personally I've found it useful to be able to apply tools like grep to mbox files.  Listing the subject lines of all the messages in a mailbox, for instance, requires just 'grep ^Subject mboxname'.  This might not seem all that important as an enduser, but it certainly has made my life easier as an admin, especially when confronted with queue problems.  You can use grep and awk to identify problematic messages and feed their IDs to a script for processing or deletion.

I also write the occasional PHP script that uses that language's IMAP functions on a mailbox.  As an example, I have a system that intercepts bounce messages for the admins of some majordomo listservers I maintain.  I can just point PHP at the mbox file and open it directly.  

If the messages were all kept in a database, I'd find it hard to do this sort of meta-processing since I'd probably have to do things like this on a message-by-message basis.

Oh, and backing up up mbox files is trivial.  Of course you can dump SQL databases to text (at least PostgreSQL and MySQL; DK about others) for backup as well.  But it's nice if someone's mailbox becomes corrupted to just pull last night's individual backup file for that user.

---

### Post by ishk on 2011-03-05
hi
thanks for all your replies. wat do you think searching effieciency of file based system.
i think database based system queries are much more efficient than file systems.

---

### Post by HermanAB on 2011-03-05
Depends on how much email you got.  If you got 30 year's worth of email, with tens of thousands of messages per user, then a database is much better.

---

### Post by BkkBonanza on 2011-03-05
Probably the main advantage to using a file based system is it gets rid of dependencies. ie. you can have a mail program without bringing in other tools. Nowadays you often have a DB system installed anyway for other uses so relying on it may not be a disadvantage.

---

