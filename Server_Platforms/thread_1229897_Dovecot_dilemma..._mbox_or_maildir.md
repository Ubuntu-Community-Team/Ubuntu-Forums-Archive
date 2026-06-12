---
title: "Dovecot dilemma... mbox or maildir??"
date: 2009-08-02
forum: Server Platforms
---

### Post by artheus on 2009-08-02
Well.. Here's my problem..

When I am using Mbox, I've noticed that the Trash and Drafts folders exists, and works like they should..

And using maildir I can set up so that I can put sub-folders, containing both sub-folders and messages, inside of the Inbox..

Well.. I want both! But I can't find a way to get both..
Could someone please help me!?

Cheers,
Artheus

---

### Post by artheus on 2009-08-02
And there is one more thing with using mbox... I can't remove folders!
It replys to me that "Target mailbox doesn't allow inferior mailboxes". But that is only when I try to delete a folder, and not when I create them..
Creating folders works fine in mbox, but I can't make subfolders, Not in the Inbox, and not in the other folders..

---

### Post by fakrulalam on 2009-08-03
mbox contains all the mail in one file, usually in /var/spool/mail folder. maildir is one-file-per-message which usually seen in qmail. It contains mail in /home/user folder with cur, new and tmp folder. This is the basic difference between mbox and maildir. 

The main benefit of using maildir is that it can give you unlimited mail support to the user. On the other hand in mbox user inbox can't be more than 2GB (As one single flat file to unix doesn't support more than 2GB).

---

### Post by artheus on 2009-08-03
Ok! Sounds great!
I've gotten it to work now by in the dovecot.conf using the "prefix = INBOX/" and "separator = /" works great..
But now it's the receiving again. Because of that I changed to maildir, the postfix smtp won't copy the incoming mail to the correct path, the postfix smtp still uses "mbox:~/mail:INBOX=/var/mail/%u" to put it as dovecot does..

I've done a little searching on the matter, and I found that it should work just by putting "home_mailbox = Maildir/" in the postfix main.cf. But then I saw that it won't work using procmail as I am using..

So.. my new question is..
**How can I get postfix to put the incoming mail into "maildir:/home/%u/Maildir" as my dovecot.conf is set up to read from?**

Cheers,
Artheus

---

### Post by gecka on 2010-11-25
> **artheus said:**
> 
So.. my new question is..
**How can I get postfix to put the incoming mail into "maildir:/home/%u/Maildir" as my dovecot.conf is set up to read from?**

Hi,

Just make postfix deliver mails to dovecot LDA witch will then deliver to your mailboxes properly.

Regards

---

### Post by druhboruch on 2010-11-25
You may also install mail-stack-delivery package.
It will setup and configure postfix and dovecot for you.

---

### Post by manolomalaga on 2013-02-02
[druhboruch]("http://ubuntuforums.org/member.php?u=184565"), many thanks.

---

