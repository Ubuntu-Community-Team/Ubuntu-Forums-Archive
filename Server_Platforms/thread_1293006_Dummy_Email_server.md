---
title: "Dummy Email server"
date: 2009-10-16
forum: Server Platforms
---

### Post by Jordanwb on 2009-10-16
What I'm looking for is a package that PHP can use to send emails (via the mail function). However the email server doesn't actually have to send the emails, just write them to some form of log file (database is fine too). Anyone know of such a package?

---

### Post by lykwydchykyn on 2009-10-16
You can just use the MTA that's installed by default, and send the emails to "someuser@localhost".  Then you can read the mails by typing "mail" at the prompt as that user.

What exactly are you wanting to accomplish?

---

### Post by Jordanwb on 2009-10-16
> **lykwydchykyn said:**
> You can just use the MTA that's installed by default, and send the emails to "someuser@localhost".  Then you can read the mails by typing "mail" at the prompt as that user.

So is that package installed by default? I don't think I selected "Email server" when installing Ubuntu Server

> **lykwydchykyn said:**
> What exactly are you wanting to accomplish?

Well when I write web scripts using PHP (I'm a web developer) I want to make sure that the email bit is working, whenever I use email in PHP.

---

### Post by lykwydchykyn on 2009-10-16
> **Jordanwb said:**
> So is that package installed by default? I don't think I selected "Email server" when installing Ubuntu Server

I could be wrong, but I think there is a mail transfer agent installed by default; Debian installs exim4, I don't know about Ubuntu.(EDIT: I think it might be nullmailer)  If not, I would suggest installing postfix.

> 
Well when I write web scripts using PHP (I'm a web developer) I want to make sure that the email bit is working, whenever I use email in PHP.

If you have something like exim or postfix installed, you should be able to send mails to local accounts.  Try this at the command line:

```

echo "test" |mail -s test $USER@localhost

```
Then type "mail" and you should see one message with the subject "test".

EDIT: all of this will be logged in /var/log/mail.log too.

---

### Post by Jordanwb on 2009-10-16
I installed Postfix and mailutils (to get the mail command) and it works with PHP just fine. Thanks. This was what I was looking for.

---

