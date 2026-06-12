---
title: "POP3 &amp; SMTP Mail Server"
date: 2005-08-13
forum: Server Platforms
---

### Post by koggo on 2005-08-13
Does anyone know any good Mail Server software?

---

### Post by bjweeks on 2005-08-13
Theres postfix.

---

### Post by koggo on 2005-08-13
Im a bit of a noob to all of this, how/where do you configure it, and can you use it for multiple domains?

---

### Post by KageKeeper on 2005-08-13
I like Courier personally :)

---

### Post by deuce868 on 2005-08-13
no offense, but setting up a proper secure mail server that is not something you go in and do overnight. You need to worry about a lot of security issues, proper DNS setup, SMTP, POP & IMAP, authentication which can lead to things like TLS and more. 

This is what I run:
Bind9
Postfix SMTP
Courier IMAP
Maildrop
amavisd-new
spamassasin
postgrey
clamav
squirrelmail

with TLS authentication on system accounts. 

The first place to start is generally at DNS.

---

### Post by pappo on 2005-08-13
You might want to take a look at SurgeMail.
For only 5 users it is free and very powerful.

[http://netwinsite.com/surgemail/](http://netwinsite.com/surgemail/)

It can handle all the anti-spam and virus protection.

---

### Post by dcostelloe on 2005-08-30
is there a configuration to assist with postfix?
Is it better than Send Mail 

Newbie at Linux SMTP and I currently run a Windows 2000 environment with Mecury32. Decided to changing over to ubuntu linux and run my web site and SMTP server.
Appreciate your time

Thanks

---

### Post by soon82 on 2005-09-02
[QUOTE=koggo]Does anyone know any good Mail Server software?[/QUOTE]


Xmailserver

---

### Post by SpooD on 2005-09-02
[QUOTE=soon82]Xmailserver[/QUOTE]
 This is where I started off when setting up a mailserver:

[http://wiki.arslinux.com/Mail_Server_FAQ](http://wiki.arslinux.com/Mail_Server_FAQ)

/Andréas

---

### Post by bjweeks on 2005-09-02
Read [this](http://www.harrysufehmi.com/phpwiki/index.php/SettingUpLinuxServer) 
its has great info on running a debian server so it should work fine. You might have to enable universe for some of the apps.

---

