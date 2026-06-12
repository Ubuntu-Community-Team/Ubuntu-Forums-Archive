---
title: "Post Fix and Mail Client Incompatability"
date: 2005-05-25
forum: Server Platforms
---

### Post by dallypost on 2005-05-25
I recently set up a server with Postfix and Courier. I can log into the server and use mutt to check and send mail without any problems. I have installed Squirrelmail and it will send an email without a problem. When I try to check my mail, it reports that inbox is empty. I also set up Balsa and Evolution and they both have the same problem finding mail on the server. Both Evolution and Balsa will send mail with no issues. Squirrelmail, Evolution and Balsa all have the same problem checking mail.

This leads me to beleive that their might be a problem with the Postfix configuration, but I cannot seem to figure out what the problem is.

Thanks

Lance Earl

---

### Post by dannysauer on 2005-05-25
Postfix sends mail.  If you can send mail, Postfix is fine.  If you have problems checking mail, then you probably have an error in the mail checking program - likely your IMAP/POP server.

Make sure that mail is delivered to the right place (either a postfix or procmail thing, probably), and then make sure that the IMAP/POP server you're using is configured to check that place.

---

### Post by LordHunter317 on 2005-05-25
Post your /etc/postfix/main.cf.

If you're using procmail, post the relevant procmailrc files.

It's possible the issue is with courier but I suspect the mail is not being delivered correctly in the first place--postfix doesn't come setup to work with courier OOB.

Posting error messages you're seeing would be immensely helpful.

---

### Post by dallypost on 2005-05-27
I modified the line in main.cf to read:

home_mailbox = Maildir/


This fixed the problem

Lance Earl

---

