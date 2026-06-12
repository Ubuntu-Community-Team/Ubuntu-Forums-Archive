---
title: "Cannot send mail outside of machine."
date: 2011-01-05
forum: Server Platforms
---

### Post by lapis_ on 2011-01-05
I am attempting to get mail working on a server, and having some trouble. I'm working with sendmail, and I am to the point where I can send and receive mail on the server (from one user account to another), but I cannot send mail from the machine to somewhere else (specifically a Google Apps GMail account).  When I try to send mail to the gmail account, I receive a "Undelivered Mail Returned to Sender" message. I've never managed any sort of mail server, and so far searching the internet hasn't helped me. Any ideas? I can post files from /etc/mail if necessary. I'm using Ubuntu Server 10.04

Thanks!

---

### Post by stygg on 2011-01-05
You need to configure postfix or exim4 to be able to send mail outside your own network. In my experience postfix seems to be standard for ubuntu, bit I prefer exim4 for some reason. Be sure to set the smtp server right because that's the one handling outgoing mail. 

/etc/exim4
or 
/etc/postfix (guess)

---

### Post by James78 on 2011-01-05
> **stygg said:**
> You need to configure postfix or exim4 to be able to send mail outside your own network. In my experience postfix seems to be standard for ubuntu, bit I prefer exim4 for some reason. Be sure to set the smtp server right because that's the one handling outgoing mail. 

/etc/exim4
or 
**/etc/postfix (guess)**
/etc/postfix/main.cf and /etc/postfix/master.cf.. Unless you were talking about the directories in which the configuration files are contained. ;)

---

### Post by stygg on 2011-01-06
> **James78 said:**
> /etc/postfix/main.cf and /etc/postfix/master.cf.. Unless you were talking about the directories in which the configuration files are contained. ;)

Yes =D>
And on exim you need to configure the update-exim4.conf.conf file and add your smtp address to the dc_smarthost line. Then run: sudo update-exim4.conf..  and maybe a /etc/init.d/exim4 restart (to be sure :)).

---

