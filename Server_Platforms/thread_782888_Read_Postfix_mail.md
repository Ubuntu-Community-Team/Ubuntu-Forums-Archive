---
title: "Read Postfix mail"
date: 2008-05-05
forum: Server Platforms
---

### Post by ngmachado on 2008-05-05
Hello all,

I'm self-learning server administration so I installed Ubuntu 8.04 LTS in a VPS. 

Then I installed Posfix to handle mail. Fine. I can send email using the command "sendmail".

Whenever I login (SSH) I receive the message: "You have mail".

If I "pico /var/mail/username" I can read the mail... but I'll receive the login message again! (meaning that the mail wasn't marked as read!).

How can I read the mail correctly without using pico? How can I delete the message?

I wouldn't like to install more packages since the VPS space is tight.

Thanks

---

### Post by augus on 2008-05-05
sudo apt-get install mailutils
try this, you can use command *mail*

---

