---
title: "Squirrelmail cannot receive email"
date: 2017-03-18
forum: Server Platforms
---

### Post by nightfrost123 on 2017-03-18
hello guys, i'm a complete beginner in this but i'm given an assignment to create a mail server. I'm using postfix, dovecot and squirrelmail for this matter. After all setup is finished, i can send emails but i can't receive them. What should I do? I have create a mx record but fear that i might be wrong.

Here is the link to the pic I saved that might help
[http://imgur.com/a/dwRyr](http://imgur.com/a/dwRyr)

any help would be appreciated

nb: the ip in the dns configuration is the ip given to me to create a mail server inside. I registered the a free domain(since this is temporary) for my given ip. And im using ubuntu 16.04

thx in advance!

---

### Post by wildmanne39 on 2017-03-19
*Thread moved to **Server Platforms**.*

---

### Post by nightfrost123 on 2017-03-19
bump

---

### Post by SeijiSensei on 2017-03-19
By default, Postfix in Ubuntu can only accept inbound connections from the localhost address.  To receive mail from any server on the Internet, you need to set
```
$mynetworks = 0.0.0.0/0
```
in /etc/postfix/main.cf.  Read this for more details: [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html)

Also, logs are your friends.  Take a look at /var/log/mail.log to see any errors Postfix generates.

---

