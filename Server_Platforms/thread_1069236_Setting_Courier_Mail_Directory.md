---
title: "Setting Courier Mail Directory?"
date: 2009-02-13
forum: Server Platforms
---

### Post by lightnb on 2009-02-13
Hi,

I have an Ubuntu 8.04 Server running Courier/postfix. It can send and receive mail ok. But theres a problem with connecting via Pop / imap.

I get the error:  "chdir Maildir failed" when trying to download messages in thunderbird. (I get the same error using telnet)

I've found references to this on the internet saying that I need to create a mail directory in the mail user's home folder. But my mail users don't have home folders. Each user does have a mail folder, under a single "mail" user, but each mail user doesn't have his own server login/account. 

Example:
/home/mail/mysite.com/webmaster
/home/mail/mysite.com/bob
/home/mail/anothersite.com/tom
/home/mail/anothersite.com/joe

I assume I need to set the Courier to find mail in this alternate directory structure, but how?

---

### Post by spiderbatdad on 2009-02-13
How are you handling the authentication, through courier or authmysqlrc?

---

### Post by lightnb on 2009-02-15
Thanks for your reply,

I'm using authmysqlrc.

I managed to get it working- I wish I could say what was the problem, but here's what I did:


```
rm /etc/courier/authmysqlrc
nano /etc/courier/authmysqlrc
```

Then I pasted someone else's working configuration file in, changed MYSQL_USERNAME and MYSQL_PASSWORD fields to my own, and rebooted.

:P So there was something wrong with my authmysqlrc file, but I'm not sure what. Anyway, problem solved!

(Now if I could only figure out why mails sent from my server to *@bellsouth.net drop off the face of the earth....._

---

