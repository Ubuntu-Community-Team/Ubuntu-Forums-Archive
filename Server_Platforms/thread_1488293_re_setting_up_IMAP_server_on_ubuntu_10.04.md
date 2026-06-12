---
title: "re setting up IMAP server on ubuntu 10.04"
date: 2010-05-19
forum: Server Platforms
---

### Post by comcraft on 2010-05-19
Im trying to setup a server using Ubuntu 10.04, I think instead Im pulling hair out.

I can see the mail from Thunderbird, I can send mail locally, however I cannot receive mail.  I have have checked the routers and everything I can think of.  I imported the mail from the old mail server and I can see it accessing it via the IP of the server.

When I look at pstree I get dovecot imap coming up.  I am unfamiliar with this.

Can anyone tell me what I need to do ?  .. or even test ?

Thanks

---

### Post by jjcv on 2010-05-20
Can you connect to the IMAP ports.

telnet <ip address> 114

or if you use TLS

telnet <ip address> 587

If you cannot connect to one of these then their could be several issues.

1.   Firewall is blocking port.
2.   Dovecot has not been correctly configures.  Check /var/log/mail.log

Pretty hard to say much else without knowing how you have configured your system.

---

### Post by comcraft on 2010-05-20
> **jjcv said:**
> Can you connect to the IMAP ports.

1.   Firewall is blocking port.
2.   Dovecot has not been correctly configures.  Check /var/log/mail.log

Pretty hard to say much else without knowing how you have configured your system.

No - I cannot connect ... 

The firewall has nothing in it 

mail.log
mail_location not set and autodetection failed: Mail storage autodetection failed with home=/home/ian
Fatal: Namespace initialization failed

I wonder if I should just install postfix and use that ..

---

### Post by TheFuturian on 2010-05-20
Postfix is for SMTP, dovecot is for POP/IMAP..

[https://help.ubuntu.com/10.04/serverguide/C/email-services.html](https://help.ubuntu.com/10.04/serverguide/C/email-services.html)

How'd you do the mail import? How have you got Thunderbird configured?

---

### Post by comcraft on 2010-05-20
> **TheFuturian said:**
> Postfix is for SMTP, dovecot is for POP/IMAP..

[https://help.ubuntu.com/10.04/serverguide/C/email-services.html](https://help.ubuntu.com/10.04/serverguide/C/email-services.html)

How'd you do the mail import? How have you got Thunderbird configured?

Yes .. thunderbird is configured ... Im using the local IP currently to get it to log in rather than via DNS mail.domainname

---

