---
title: "Error connecting to IMAP server"
date: 2013-05-15
forum: Server Platforms
---

### Post by mrowder on 2013-05-15
Hi all, 
I install postfix, dovecot and squirrelmail in my ubuntu. 
when I login squirrelmail , I saw this message.
"Error connecting to IMAP server: localhost.
111 : Connection refused"

My /var/log/mail.log is
May 15 14:20:33 tkfsh postfix/master[8097]: terminating on signal 15
May 15 14:20:34 tkfsh postfix/master[8491]: daemon started -- version 2.9.6, configuration /etc/postfix

How can I solved this problem?
Thanks,

---

### Post by SeijiSensei on 2013-05-15
deleted

---

### Post by SeijiSensei on 2013-05-15
> "Error connecting to IMAP server: localhost. 111 : Connection refused"
Why are you using port 111?  IMAP listens on 143.  Perhaps there is a typo in the SquirrelMail configuration file?

---

### Post by mrowder on 2013-05-15
Thanks for u suggestion.
I check my SquirrelMail configuration file imap already listen port 143.
But server stiil have the problem.

---

### Post by mrowder on 2013-05-16
I cat my /var/log/mail.log 
postfix/master[16097]: terminating on signal 15
postfix/master[16255]: daemon started -- version 2.9.6, configuration /etc/postfix
Is this log something problem?

---

### Post by lisati on 2013-05-16
There could be a typo in the configuration file for dovecot. Some information on setting it up can be found here: [https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)

---

