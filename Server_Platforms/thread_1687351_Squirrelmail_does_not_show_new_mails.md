---
title: "Squirrelmail does not show new mails"
date: 2011-02-13
forum: Server Platforms
---

### Post by skink260 on 2011-02-13
Hello,

I have installed ubuntu 10.10 server which runs postfix and dovecot and squirrelmail for emails.

There is something that i could not solve by myself.
Squirrelmail sends emails fine however it does not show the mails that are received. I can see new mails via ssh in /var/mail.

What could be the possible reason for this? Please help.

Thanks.

---

### Post by elico on 2011-02-14
can you try another IMAP client such as thunderbird?

---

### Post by SeijiSensei on 2011-02-14
Did you run the conf.pl script as root with sudo and configure the IMAP server section?  Are you sure dovecot is running?

Try running "telnet localhost 143" from a command prompt.  Do you get the  banner "* OK Dovecot ready." in reply?

---

