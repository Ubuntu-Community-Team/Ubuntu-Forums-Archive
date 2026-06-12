---
title: "command line email client for server"
date: 2010-07-21
forum: Server Platforms
---

### Post by three_jeeps on 2010-07-21
I am looking for command line based mail client that can send & receive email through Gmail (smtp, imap) - I do *not* want to run a mail server (MTA)on my Ubuntu server 8.04.  

Furthermore, I want the capability to do a) and possibly b):

a) have an interface in the mail client that will allow it to detect an event and have it send an email message through gmail to a specified user(s).  Ideally, periodically parse a text file for a keyword and if present, send a message

b) send a message based on a scheduled action from cron. For example, a crontab entry that runs a backup.

Any suggestions & approaches are appreciated.
thank you!
-J

---

### Post by wojox on 2010-07-21
Take a look at [Pine]("http://en.wikipedia.org/wiki/Pine_%28e-mail_client%29")

---

### Post by three_jeeps on 2010-07-21
> **wojox said:**
> Take a look at [Pine]("http://en.wikipedia.org/wiki/Pine_%28e-mail_client%29")

Alpine looks like it may work...fits the CL requirement, BUT not clear how to automatically have it send a message from an external trigger....
Suggestions????

---

### Post by HermanAB on 2010-07-21
Try Mutt.

---

### Post by spynappels on 2010-07-21
+1 for mutt

---

