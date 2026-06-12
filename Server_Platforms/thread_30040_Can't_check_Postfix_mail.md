---
title: "Can't check Postfix mail"
date: 2005-04-27
forum: Server Platforms
---

### Post by dallypost on 2005-04-27
I just finished setting up my first internet server. Most aspects are working pretty well, however, email is broken. I installed Postfix and went through the config files and set them up as recommended at postfix.org.   I cannot check my mail from a remote computer. Evolution returnes the message "Failed to read a valid greeting from POP server mail.dallypost.com." I checked netstat -pautu and did not see anything that seemed to be related to postfix. Do I need to open a port or something. I am new to this and for the moment, completely stumped.

Lance

---

### Post by ape on 2005-04-27
Postfix does not provide a POP server.  You would need to install a package that provides this.  Open up a shell and issue the command `apt-cache search pop3 | more` and you'll get a listing of the packages you can choose from.

---

### Post by nemin on 2005-04-27
[QUOTE=dallypost]I just finished setting up my first internet server. Most aspects are working pretty well, however, email is broken. I installed Postfix and went through the config files and set them up as recommended at postfix.org.   I cannot check my mail from a remote computer. Evolution returnes the message "Failed to read a valid greeting from POP server mail.dallypost.com."[/QUOTE]Postfix is just a SMTP server, you can't check your mail with it. You have to install a POP or IMAP server to read your mail. When you don't know wich to choose, read a link like [https://hdc.tamu.edu/reference/documentation/?section_id=436](https://hdc.tamu.edu/reference/documentation/?section_id=436). I'd advise courier, see [http://www.courier-mta.org/](http://www.courier-mta.org/), it's quite easy to setup. Mention you'll only need to install the courier-imap or courier-pop server. Good luck :)

---

