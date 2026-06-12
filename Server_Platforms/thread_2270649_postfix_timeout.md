---
title: "postfix timeout"
date: 2015-03-24
forum: Server Platforms
---

### Post by john_paul2 on 2015-03-24
How do you increase the timeout from Postfix to a smarthost?  I'm worried that by the time the e-mail is scanned and attempted to transfer to our Exchange server from Postfix, the delay is already past and it is not delivered.   This only happens on messages that takes about 3-4 minutes, which are larger e-mails between 10-15 Megs.

---

### Post by SeijiSensei on 2015-03-24
If both servers are on the same network, there's some deeper problem.  It shouldn't take that long to send a 10-15 MB message over a Ethernet connection.  I just moved a 15 MB file from a server to a desktop client; it took less than five seconds.

Is it the scanner that's taking all the time?  I use MailScanner with ClamAV and SpamAssassin.  It takes my server just a few seconds to scan each message for viruses and spam and forward them along.  Can you tell us more about what you're using to scan messages?

---

