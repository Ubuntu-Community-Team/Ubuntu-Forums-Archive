---
title: "Postfix SMTP Server Not Recieving Mail"
date: 2009-07-10
forum: Server Platforms
---

### Post by guywithcable on 2009-07-10
Hello all,

I have a Postfix server, which is using Dovecot for IMAP/POP access (dovecot-postfix package installed). I can send mail from it successfully, but when I send mail to it, it doesn't work. I've followed the following tutorials, and nothing I've tried has worked:

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)
[https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)

---

### Post by guywithcable on 2009-07-10
Anybody have any ideas?

---

### Post by guywithcable on 2009-07-10
Fixed it. Looks like in order to access Dovecot from another host you have to uncomment the "listen = *" line in its config file. I missed that note when I read through the tutorial. ;)

---

### Post by windependence on 2009-07-10
Just FYI, SMTP is for outgoing mail. Dovecot is what is receiving your mail.

-Tim

---

### Post by guywithcable on 2009-07-11
> **windependence said:**
> Just FYI, SMTP is for outgoing mail. Dovecot is what is receiving your mail.

-Tim

Actually SMTP does both. An SMTP server is used to transfer mail to another SMTP server, which can either transfer it to another server, or deliver it to a user's mailbox. Dovecot doesn't actually receive any mail, it delivers new mail to the user through either POP or IMAP. The problem was that Dovecot was not delivering my mail, so I was wrong with the title of the thread, but that is something Postfix does.

---

### Post by windependence on 2009-07-12
Well, Postfix is an MTA so yes, it transfers mail pure and simple. I wasn't tryng to split hairs with you, just figure out what was going on to help you. As I said, the problem was with dovecot and not your SMTP which you confirmed. I stand by my comment that SMTP is used to send mail out. :-)

-Tim

---

