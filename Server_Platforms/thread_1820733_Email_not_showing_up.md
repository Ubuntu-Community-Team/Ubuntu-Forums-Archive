---
title: "Email not showing up?"
date: 2011-08-08
forum: Server Platforms
---

### Post by spy_1134 on 2011-08-08
Hey guys,
I'm working on setting up an e-mail server for me and a few friends off of an Ubuntu box I have.

As far as I can tell, IMAP is working fine. I can connect to it and everything seems to be working properly.

Here's the problems:
 - All of the new mail I get is being put into /var/mail/<username> and IMAP is looking for Maildirs I think. Is there any way to redirect the mail into the maildirs? Or is there a better way to do this?
- SMTP server doesn't seem to be working. Thunderbird says that the connection timed out.

Info:
Postfix and Dovecot
Ubuntu Server 10.04.2

---

### Post by spy_1134 on 2011-08-08
I fixed the SMTP server by purging configuration and starting over.

Now, my only problem is that new messages don't show up in IMAP.
Does anyone know how to fix this?
I know that the system is receiving the mail, but IMAP won't show it.

---

### Post by spy_1134 on 2011-08-08
Nevermind, fixed it myself. As usual. :P
I had to clear my mailbox_command in /etc/postfix/main.cf.

---

### Post by Vishal Agarwal on 2011-08-08
Can you pls inform what u did for this solution ?

---

