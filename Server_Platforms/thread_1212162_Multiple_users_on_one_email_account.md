---
title: "Multiple users on one email account"
date: 2009-07-13
forum: Server Platforms
---

### Post by Celauran on 2009-07-13
I'm trying to keep my email in sync across multiple machines. My ISP uses POP, so I'm trying to approximate IMAP behaviour as best I can. Currently, I've got my server machine retrieving the mail from ISP using fetchmail, procmail is sorting the mail to /var/mail/me, and Dovecot allows my desktop and laptop to effectively share the inbox.

Where I'm stuck is on sending mail. I don't want a bona fide SMTP server to be running on my machine, but I would like email sent from my laptop to be visible as sent on my desktop and vice versa. Any ideas/pointers on how this would be done?

---

