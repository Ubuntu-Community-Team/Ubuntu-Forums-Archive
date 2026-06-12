---
title: "Postfix + SpamAssassin, forward spam mails to 1 mailbox"
date: 2005-11-23
forum: Server Platforms
---

### Post by Tonik on 2005-11-23
Hi, can someone give me a working example of Postfix + SpamAssassing configured in such away that all mail marked as spam goes into one mailbox and not to the original recipient?

I googled and it seems that people do it with procmail, but the weird procmail syntax is beyond me.  Sensible procmail docs are nowhere to be found, and the attempts to learn procmail by studing existing configs is likely to send me to a mental hostpital fairly quickly.

Alll I need is to make spam go to one mailbox.  Please.

(just in case, I'm using postfix virtual domains + dovecot IMAP server)

---

### Post by casper_2095 on 2005-11-23
Is the postfix filtering of any use to you?

file:///usr/share/doc/postfix/html/BUILTIN_FILTER_README.html
file:///usr/share/doc/postfix/html/header_checks.5.html
file:///usr/share/doc/postfix/html/FILTER_README.html

---

### Post by cactus on 2005-11-23
You might give MailScanner a try. I have a client that recommended it, and It integrates spamassasin, clamav, and postfix together. It does do a little wonkiness with the queues, but it hasn't been *too* much of a problem for me yet.
Otherwise, I would recommend using amavisd-new. That has proven foolproof for me in the past.

---

### Post by Tonik on 2005-11-24
casper_2095, thanks a lot!

I added this line to /etc/postfix/main.cf:
```
header_checks = pcre:/etc/postfix/header_checks
```

and this is my /etc/postfix/header_checks:
```
/^X-Spam-Flag: YES/                     REDIRECT spam@my_domain
```

Looks so easy once you know how to do it.

I'll check out MailScanner, too.  I will need ClamAV anyway.

---

