---
title: "Mailscanner hangs once a day"
date: 2006-03-08
forum: Server Platforms
---

### Post by tepegoz on 2006-03-08
Dear all,
Although this forum is not a debian forum, I am sure that many of you are using debian in your servers.  So I think that there are people out there who can help me with my problem.

I am using postfix and mailscanner. Clamav, bit defender are working on mailscanner. 
The problem is this: Mailscanner hangs aproximately once a day. It does not scan the mails in the queue for hours until I restart it.  Once it is restart, it scans everything and comes back to normal operation for a while. And so on.

No error or a helpful warning, or something related to the problem in mail.log, mail.warn, or mail.err.

Has anybody faced with similar problem?
Thanks

---

### Post by nocturn on 2006-03-08
I'm running MailScanner with SpamAssassin and ClamAV on my Ubuntu server.
It has been running as long as the server was up, that is currently 42 days.

Maybe bitdefender is the cause?

---

