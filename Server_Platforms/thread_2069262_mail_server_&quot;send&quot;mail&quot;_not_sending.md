---
title: "mail server &quot;send&quot;mail&quot; not sending mail"
date: 2012-10-10
forum: Server Platforms
---

### Post by micahpage on 2012-10-10
I am trying to get the "mybb" forums to send email verification upon registration. The email log in their area shows no errors. the apache log also shows no errors. 

I have done the PHP self mail test, it says the mail was sent but it is not sent (or received).
Currently i have sendmail installed. 

Is there an apache setting that i am missing?

---

### Post by Bachstelze on 2012-10-10
E-mail is complicated. Tell us more about your setup: where is the machine (home? datacenter?).

---

### Post by micahpage on 2012-10-13
> E-mail is complicated.I noticed, i was spending a couple days on it, trying sendmail then smtp, and gettign no where with it. 

It is a home server.

---

### Post by cool110 on 2012-10-13
Most spam filters will reject all mail from IP addresses belonging to residential ISPs. I would recommend using postfix and relaying mail through your ISP's smart host if they provide one or a Gmail account.

[http://ubuntu-tutorials.com/2008/11/11/relaying-postfix-smtp-via-smtpgmailcom/](http://ubuntu-tutorials.com/2008/11/11/relaying-postfix-smtp-via-smtpgmailcom/)

---

### Post by sasa.tomic on 2012-10-25
Hi, configuring postfix (sendmail) is certainly not easy.
I made a small user-friendly script for a no-questions-asked  installation and configuration of postfix with Gmail.

The script configures postfix to relay mail to smtp.gmail.com (which will send your emails to the world).
Check out the [https://gist.github.com/3952294](https://gist.github.com/3952294)
and please tell me if it works for you (or not)

P.S. I checked the script on Ubuntu 12.04, but it should work on previous versions as well. Before running the script, uninstall everything you manually configured on your machine (e.g. exim4 maybe), and also, you should consider purging postfix with
```

sudo apt-get purge postfix
```

---

