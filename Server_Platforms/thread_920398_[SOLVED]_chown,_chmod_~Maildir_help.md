---
title: "[SOLVED] chown, chmod ~Maildir help"
date: 2008-09-15
forum: Server Platforms
---

### Post by volkswagner on 2008-09-15
After much reading, config and hair pulling I have a working mail server.

From numerous how-to's, I have Postfix, courier, on LAMP.  

My last hurdle is proper handling of mailbox directory owner and permissions.

For me to read new mail I have to chmod -R 777 my mail directory.  If I don't chmod evolution does not pick up new mail and squirrel mail sees the new mail as unreadable. 

How should I set up owner and permissions for /home/myuser/Maildir, for both security and function?
Should the owner be me or postfix, do I need to add myself to postix group?

ls -alt /home/user/Maildir
```
total 48
drwxrwxrwx  2 eric    root    4096 2008-09-15 08:12 tmp
-rwxrwxrwx  1 virtual virtual  219 2008-09-15 07:29 courierimapuiddb
drwxrwxrwx  2 eric    root    4096 2008-09-15 07:29 cur
drwxrwxrwx  2 eric    root    4096 2008-09-15 07:29 new
drwxr-xr-x  8 eric    eric    4096 2008-09-14 19:22 ..
drwxrwxrwx 10 eric    eric    4096 2008-09-14 19:17 .
-rwxrwxrwx  1 virtual virtual   36 2008-09-14 19:17 courierimapsubscribed
drwxrwxrwx  6 eric    root    4096 2008-09-14 14:44 .Drafts
drwxrwxrwx  6 eric    root    4096 2008-09-14 14:44 .Trash
drwxrwxrwx  6 eric    root    4096 2008-09-14 14:44 .Templates
drwxrwxrwx  6 eric    root    4096 2008-09-14 14:44 .Sent
drwxrwxrwx  2 eric    virtual 4096 2008-09-14 14:29 courierimapkeywords
```



Thanks in advance

---

### Post by volkswagner on 2008-09-15
I think I should rephrase my question.

How do I get postfix to make the mail readable?  How do I get postfix to set the proper permissions for new mail?

---

### Post by volkswagner on 2008-09-15
I have followed way too many how-to's.  I hope this is my last hurdle.

Error was setting uid in mysql to 5000.  My uid is 1000, and I am not using virtual mailboxes.  Since changing mysql, I can now leave my Maildir at chmod 700.

Force feeding myself to learn.

:)

---

### Post by pqrs541 on 2008-09-16
The Weather:[buy wow gold](http://www.mmoinn.com)  It's so dry, the trees are bribing the dogs. It's been hitter?s a goat's butt in a pepper patch.  Wintry roads are said to be "slicker than otter snot. [wow gold](http://wowus.mmoinn.com/index.do?PageModule=OrderForm_new)[wow gold](http://woweu.mmoinn.com/index.do?PageModule=OrderForm_new) [World of warcraft Gold](http://www.mmoinn.com)[wow gold](http://www.mmoinn.com)

---

