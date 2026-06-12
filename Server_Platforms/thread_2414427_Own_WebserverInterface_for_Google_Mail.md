---
title: "Own Webserver/Interface for Google Mail"
date: 2019-03-10
forum: Server Platforms
---

### Post by ex0nuss on 2019-03-10
Hey,

I have currently a old laptop which running Ubuntu Server 18.10. It acts as a OpenVPN Server.
On one of my devices I am not able to use the "mail.google.com" website for my e-mails. This is due to locked proxy settings. I am also not able to use a (portable-)software like Thunderbird.

I thought that I could run on my Ubuntu Server at home a Webinterface with login which connects via IMAP to the Google Mail Server. 
Probably the best way is, that my Server downloads the mail on the local hard-drive. Otherwise the proxy could perhaps cause problems.

Hopefully you guys have ideas how the get this working. Like software recommendations etc.
I am relatively new to Linux but I am willing to learn a low :)

Thanks for answering in advance.
Regards, Max

---

### Post by TheFu on 2019-03-16
Some options.
* squirrelmail  / redmail - web interfaces
* postfix / exim / sendmail - MTAs (SMTP)
* fetchmail - poll IMAPS 

I've been using Zimbra, which has an ability to be an IMAPS client, but that is way overkill and much too complex and has significant server requirements, compared to the others, for your needs. 

If I where you, I'd do this.
* Setup postfix to send email outbound from squirrelmail
* Setup fetchmail to poll gmail's IMAP services and pull copies local.  You'll need to tell google to allow imaps access to email and they will nag about it being unsafe.
* Dovecot might be needed for squirrelmail to have a local IMAP server to talk with. IDK.

There is a send-only SMTP server - I don't remember the exact name  ssmp .. smmp ... just search these forums for "simple gmail sending email". Basically, it can only send email using 1 gmail account for authentication.

I suspect most people would just use their cell phones to access gmail when away from home. Much easier.

---

### Post by TheFu on 2019-03-19
Found this: [https://help.ubuntu.com/community/EmailAlerts](https://help.ubuntu.com/community/EmailAlerts)  sSMTP.

---

