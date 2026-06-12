---
title: "New problems with new install mail server"
date: 2010-02-19
forum: Server Platforms
---

### Post by LMSSML on 2010-02-19
Hi people,

I've followed the manual with 

> [http://flurdy.com/docs/postfix/#config-simple-firewall](http://flurdy.com/docs/postfix/#config-simple-firewall) How to set up a mail server on a GNU / Linux system

but then I could create mailbox with phpmyadmin using mysql commands and in maildb database althouth every user I create on DB if I try with squirrel or even with roundcube none of them work.

I can see it in /var/spool/mail/virtual/<username> is not created for new users.

Is there any admin software (like webmin) to create user accounts and mailbox ?

I think I missed a step creating user accounts but I couldn't find what is missing.

Just to referre that I have a user created and this user works but hte new ones dosen't work and for the first user the folder for user was created automatically.

log when sent a message:

>  NOQUEUE: reject: RCPT from localhost.localdomain[127.0.0.1]: 554 5.7.1 <localhost.localdomain[127.0.0.1]>: Client host rejected: Access denied; from=<email> to=<email> proto=ESMTP helo=<mail.example.pt>
Feb 19 11:46:44 mail postfix/smtpd[6284]: disconnect from localhost.localdomain[127.0.0.1]

Log of roundcube

 > SMTP Error: SMTP error: Failed to add recipient 'test@gmail.com' in /usr/share/roundcube/program/steps/mail/func.inc on line 1296 (POST /roundcube/?_task=mail&_action=send)



Thanks in advanced for the help .
LMS

---

### Post by LMSSML on 2010-02-19
anyone 

To help ?

---

### Post by windependence on 2010-02-19
[http://www.zimbra.com/downloads/os-downloads.html](http://www.zimbra.com/downloads/os-downloads.html)

VMware now owns Zimbra.

-Tim

---

