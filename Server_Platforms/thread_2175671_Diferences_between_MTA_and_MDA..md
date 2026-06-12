---
title: "Diferences between MTA and MDA."
date: 2013-09-20
forum: Server Platforms
---

### Post by isirguezglez-h on 2013-09-20
Hi!!

I got a server to learn, but I feel confused with the email server.

An MTA, e.g. Postfix, is used to send and receive email. Emails are stored in the mailbox.

But I'm not sure with MDA, e.g. Dovecot, some tutorials says that it's used to delivery emails to the mailbox of the users (I thought that MTA do that), another ones say that it's used to get access to mailbox over internet with a client.

I need a teacher :-|

---

### Post by luciano_rinetti on 2013-09-21
I'm not a teacher on this subject, but i have had the same doubts.
I can suggest a book that help me a lot  to administer my little mail server in my company,
 because the book has a grounding in the way MTA, MDA, MUA, antispam, etc. work together to realize a working mail server:
"The Exim SMTP mail server" 2nd Ed. by Philip Hazel (UIT Cambridge ed.)
Exim is well documented and feature-rich MTA but the best thing you can do is read the:
[www.exim.org](www.exim.org)
The book is focused on Exim but not only. In simple words: it worths the money.
Good luck.

---

### Post by newbie-user on 2013-09-21
There are three parts to mail transport. The Mail Transport Agent (MTA), such as Postfix, is responsible for sending email to the correct destination. The Mail Delivery Agent (MDA) is what receives the incoming email and sorts it into user mailboxes. The Mail User Agent (MUA) is the email client that retrieves the email from the user mailboxes and presents it to the user.

Dovecot provides POP3 and IMAP functionality while also providing MDA functionality. The POP3 and/or IMAP functionality is required in order for an email client to access the user's mailbox.

---

### Post by aerokid240 on 2013-09-26
As stated before, there are MTA, MDA, and MUA. Postfix has both MTA and MDA (more specifically LDA, local delivery agent)capabilities. It's own MDA/LDA program is called "local" if i remember correctly. This program itself is not feature rich and is very bare bones. You can't recieve emails remotely with postfix alone. You will need a pop3 or imap daemon for that.

---

