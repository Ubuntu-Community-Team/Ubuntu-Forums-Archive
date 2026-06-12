---
title: "Easy smtp server"
date: 2011-11-18
forum: Server Platforms
---

### Post by RedSingularity on 2011-11-18
Anyone know of an easy to set up smtp server or something like it?  I want to set it up on my server and have notifications sent to my email address.  Command line options are fine.  I just need something simple though.  Sendmail and postfix seem like overkill for me.  I only want the ability to send mail to my GMX account.  No need to receive mail.  I see webmin has options for this but it wants postfix or sendmail set up in order to send notifications.

---

### Post by collisionystm on 2011-11-18
install mailutils

sudo apt-get install mailutils

send an email like this

> echo "This is the body of my message. Wow this is so simple" | mail -s "This is my subject line!" [email]me@mydomain.com[/email]

---

### Post by RedSingularity on 2011-11-18
Any configuration needed after install?

---

### Post by collisionystm on 2011-11-19
no

---

### Post by HermanAB on 2011-11-19
Howdy,

The easiest mail server is Citadel. It has a script called appropriately easyinstall, which makes installation a no brainer.

[http://citadel.org](http://citadel.org)

---

### Post by rubylaser on 2011-11-19
For system emails, I just setup [sSMTP]("http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp"), and bounce my emails off my Gmail account.  Couldn't be easier if you use Gmail.

---

### Post by RedSingularity on 2011-11-20
Thanks everyone :)

---

