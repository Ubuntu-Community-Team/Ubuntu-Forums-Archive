---
title: "Internal Mail Server to Remote"
date: 2014-05-06
forum: Server Platforms
---

### Post by Nixforce on 2014-05-06
Hi,

Im setting up an internal system to help me manage my work (Im developing the system in CFML, my prefered language) What im trying to figure out is how i would be able to do this.

My hosting company said they can create a catchall mailbox for me, and i want to pull the mail from it onto my local Ubuntu Server, and my system will then seperate the mail. 

The emails will be unique per job, ie [email]job-123@domain.com[/email], the 123 will be my ID i link the email to the record in the database. 

Can the mail server i setup pull a catchall account, and seperate the emails ?

Has anyone done something similar and have suggestions?

I want the internal mail server to relay via my hosting company.

---

### Post by SeijiSensei on 2014-05-06
Use [fetchmail]("http://fetchmail.berlios.de/").  It's designed to poll remote servers, split up a mailbox into separate messages, and deliver them to various addresses.

Here's a [post about setting it up with Postfix and dovecot]("http://ubuntuforums.org/showthread.php?t=1015150").

---

### Post by vhinz on 2014-05-07
I second SeijiSensei, use fetchmail or getmail depending on what will work for you or where you are comfortable with. I used getmail before just because the system I was using isn't compatible with fetchmail (or I can't make it to work properly)

---

### Post by lisati on 2014-05-07
One option you might want to look into using [VERP]("http://en.wikipedia.org/wiki/Variable_envelope_return_path"). This lets you set up a single email account, say for example JOB, and then use an email address like [email]job+123@example.com[/email] on outgoing email. Then when you are checking incoming email, you can use some kind of filtering arrangement to seaparate what appears between the + and the @ and redirect the email to an appropriate folder and/or alternative email address.

---

