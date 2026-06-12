---
title: "Email problem in Ubuntu/Linux - What's a Postmaster???"
date: 2006-10-17
forum: The Cafe
---

### Post by emarkay on 2006-10-17
----- Transcript of session follows -----
... while talking to mail.sourceforge.net.:
>>> >>> DATA
<<< 550-Postmaster verification failed while checking <xxx@xxxxxx.com>
<<< 550-Called:   xx.xx.xxx.xx
<<< 550-Sent:     RCPT TO:<postmaster@xxxxxxx.com>
<<< 550-Response: 550 unknown user <postmaster@xxxxxxx.com>
<<< 550-Several RFCs state that you are required to have a postmaster
<<< 550-mailbox for each mail domain. This host does not accept mail
<<< 550-from domains whose servers reject the postmaster address.
<<< 550 Sender verify failed
550 5.1.1 <hplip-help@lists.sourceforge.net>... User unknown
<<< 503 valid RCPT command must precede DATA

This is the second time I have seen this when sending email in Ubuntu.  I have,  in over 10 years of WWW-ing, never seen this before!

What does this mean and how can I correct it and get mail to these folks??

---

### Post by bonzodog on 2006-10-17
The postmaster is the mailer daemon. What that message is telling you is that you must have a postmaster address on your mail server to confirm mails, otherwise it will not accept them from you.

---

