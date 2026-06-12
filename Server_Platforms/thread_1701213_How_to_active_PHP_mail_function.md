---
title: "How to active PHP mail function?"
date: 2011-03-06
forum: Server Platforms
---

### Post by acastrolorenzo on 2011-03-06
Hi everyone,

I´ve installed an 10.10 ubuntu server, and there some CMS working on PHP.
I´ve LAMP installed.

Everything its ok, except the mail sender. It uses PHP mail function, but doesnt works.

Any idea?
Thanks a lot :)

---

### Post by BkkBonanza on 2011-03-06
It's been a while but if I recall, PHP Mail function uses and depends on **sendmail** being installed (or an equivalent replacement). So step one is to make sure that you have sendmail installed. Then check the config options to be sure they are correct, see this page, [http://th2.php.net/manual/en/mail.configuration.php](http://th2.php.net/manual/en/mail.configuration.php)

sudo apt-get install sendmail

As it says in the docs, if you have a different replacement mail program installed then make sure the sendmail "wrapper" is also installed and working. This will add a script or link to emulate sendmail. On Ubuntu it may be exim that is installed but it usually has a sendmail wrapper.

So a quick test would be to type sendmail at the command prompt and see what it tells you.

---

### Post by acastrolorenzo on 2011-03-06
Thanks BkkBonanza!, just install sendmail and works. But two problems:

1º All sent mails appears only on SPAM folder. 

2º When send an email it goes very very slow. Any idea?.

Thanks again :D

---

### Post by BkkBonanza on 2011-03-06
Not sure why it's slow. I think sendmail is a bit slow but I haven't used it for years now. I use a php smtp mail function nowadays. I'd look into configuration to see if there is a problem that causes retries.

Regarding spam it may be you need to put more attention into the "from" and "reply-to" parameters. If they aren't valid or don't match with the sending IP address you may get flagged as spam or even bounced by some servers. Just going on memory, look at the "-f" option. See the advanced options section on the mail docs page, [http://th2.php.net/manual/en/function.mail.php](http://th2.php.net/manual/en/function.mail.php) for more info. I recall having to fiddle with that to get successful results.

---

### Post by acastrolorenzo on 2011-03-06
Follows here: [http://ubuntuforums.org/showthread.php?p=10528812#post10528812](http://ubuntuforums.org/showthread.php?p=10528812#post10528812)

---

