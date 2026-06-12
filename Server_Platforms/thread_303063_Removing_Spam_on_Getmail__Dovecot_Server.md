---
title: "Removing Spam on Getmail / Dovecot Server"
date: 2006-11-19
forum: Server Platforms
---

### Post by NobodySpecial on 2006-11-19
I have a Dapper server that retrieves mail from my ISP POP3 with Getmail and stores as Maildir.  Dovecot then runs as IMAP to Thunderbird or Evolution.

My ISP runs Spamassain and marks suspected Emails by adding "***SPAMTAGPTD" to the subject header.  One example:
"Subject: ***SPAMTAGPTD: but its capability makes"

If I open Thunderbird, it will spot these and move then into the Junk folder.

My question is this: is there a program I can run (either standalone or linked through Getmail or Dovecot) that will look at the mail in my Maildirs and find the ones with the Spam marking and move them directly to the Junk folder?  I would like this process done before opening Thunderbird.  That way I don't have to look at all the spam come through when running [Mail-Notify]("http://www.nongnu.org/mailnotify/") on my desktop.

Thanks for any help.

---

