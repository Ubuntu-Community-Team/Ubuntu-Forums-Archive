---
title: "Postfix, how to solve these errors?"
date: 2011-11-25
forum: Server Platforms
---

### Post by Luxik on 2011-11-25
hi, in logwatch log I found these lines:

unverified_recipient_tempfail_action = defer_if_permit
unverified_sender_tempfail_action = defer_if_permit 
unknown_address_tempfail_action = defer_if_permit 
unknown_helo_hostname_tempfail_action = defer_if_permit 

I was looking on Google but I haven't find the real solution how to fix these issues.
Thank you.

---

### Post by Doug S on 2011-11-25
I do not use logwatch, and so am not familiar with how it may or may not take var/log/mail.warn messages and translate them into what you are seeing. However, if you are going to have a publc facing postfix, then you will constantly get warnings as spammers try to send e-mails and relay e-mail and ...
 
Edit: Oh, and welcome to Ubuntu forums.

---

### Post by Luxik on 2011-11-26
> **Doug S said:**
> I do not use logwatch, and so am not familiar with how it may or may not take var/log/mail.warn messages and translate them into what you are seeing. However, if you are going to have a publc facing postfix, then you will constantly get warnings as spammers try to send e-mails and relay e-mail and ...
 
Edit: Oh, and welcome to Ubuntu forums.

Man, I really dunno what r u talking about :D

---

### Post by Doug S on 2011-11-26
It was not my intent to just add confusion, I was just trying to help.
If you put a MTA (Mail Transfer Agent), such as postfix, on line on internet, then you will get warning messages in the log files, typically located in /var/log/mail.log. These undesired email attempts will start shortly after your MTA is on-line and they will never stop. There are many automated systems that troll internet looking at everybody's port 25 and then trying to send email to them or relaying emails via them or whatever.
I am saying that these entries in your log file are a good thing, because postfix decided not to allow the e-mail.
What I do not know (because I have never used logwatch), is if the logwatch entires you listed were actually translated from the /var/log/mail.warn file or if they are from somewhere else. Hopefully another forum contributor that is familar with logwatch can help with that part.
I hope this helps, but please persist if not.

---

### Post by Luxik on 2011-11-26
> **Doug S said:**
> It was not my intent to just add confusion, I was just trying to help.
If you put a MTA (Mail Transfer Agent), such as postfix, on line on internet, then you will get warning messages in the log files, typically located in /var/log/mail.log. These undesired email attempts will start shortly after your MTA is on-line and they will never stop. There are many automated systems that troll internet looking at everybody's port 25 and then trying to send email to them or relaying emails via them or whatever.
I am saying that these entries in your log file are a good thing, because postfix decided not to allow the e-mail.
What I do not know (because I have never used logwatch), is if the logwatch entires you listed were actually translated from the /var/log/mail.warn file or if they are from somewhere else. Hopefully another forum contributor that is familar with logwatch can help with that part.
I hope this helps, but please persist if not.

Thank u mate, I took a look at log files, but no one of these lines I've found.
interesting, where did the logwatch take that from? :D lol.

Okey, but even so, idk how to solve this. 
But I was searching the answer at google, and I found it might be because of this:

smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination

is there something wrong? MMM :|

---

### Post by Doug S on 2011-11-26
It looks as though you might be using SASL authentication, if you have that line in your /etc/postfix/main.cf file. I don't use it (my postfix configuration is basic), and I will have to defer to others.

---

### Post by lisati on 2011-11-26
> **Luxik said:**
> hi, in logwatch log I found these lines:

unverified_recipient_tempfail_action = defer_if_permit
unverified_sender_tempfail_action = defer_if_permit 
unknown_address_tempfail_action = defer_if_permit 
unknown_helo_hostname_tempfail_action = defer_if_permit 

I was looking on Google but I haven't find the real solution how to fix these issues.
Thank you.

Those lines look like something you'd put in postfix's main.cf configuration file. They are explained here: [http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html)

edit: I would be surpised if those lines, as presented here, would appear in a log file.

---

### Post by Luxik on 2011-11-27
> **lisati said:**
> Those lines look like something you'd put in postfix's main.cf configuration file. They are explained here: [http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html)

edit: I would be surpised if those lines, as presented here, would appear in a log file.

u mean, this one line misses? in my main.cf file :

**access_map_defer_code = 450 **

---

