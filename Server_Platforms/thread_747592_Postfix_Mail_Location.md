---
title: "Postfix Mail Location"
date: 2008-04-06
forum: Server Platforms
---

### Post by DrumWizMV on 2008-04-06
I telnet to localhost and send mail to myself but I cant find where it goes.     Is there a default location or do I need to add a line to a config file?

---

### Post by Dr Small on 2008-04-06
Generally, mine goes to /var/mail/user

---

### Post by DrumWizMV on 2008-04-06
there is nothing in /var/mail

---

### Post by Dr Small on 2008-04-06
Ok, what about /var/spool/mail ?

---

### Post by HermanAB on 2008-04-06
The best way to test mail systems is with 'telnet', 'mail' and 'mutt':
$ mutt -f /var/spool/mail/yourusername

---

