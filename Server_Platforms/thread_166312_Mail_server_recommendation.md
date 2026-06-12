---
title: "Mail server recommendation"
date: 2006-04-26
forum: Server Platforms
---

### Post by el3ktro on 2006-04-26
Hi,
our company currently uses an external mailserver (POP/SMTP), but this mail provider constantly has problems, so we decided we want to have our own. I'm privately running a mailserver für 50+ people (Postfix, Courier-IMAP, Amavis, Spamassassin, ClamAV ...) so I have experience with setting such a thing up and making/keeping it to work properly. I just have no experience concerning the hardware. We're receiving/sending around 10.000 mails per day currently. I'd like to have Postfix running for SMTP, and Courier-IMAP (no POP server). All mails should be spam- and virus-scanned.

Does anybody of you have some experience of how powerful the hardware should be for such a server? We're thinking of having our own in-house mailserver, or renting our own root server somewhere and let everything run there. What kind of hardware would you recommend? How resource-hungry is Postifx, Courier, Amavis?


Tom

---

### Post by mjm115 on 2006-04-26
Anything above a Pentium 3 or AMD Athlon should be sufficient for what you're looking for.  I would go with at least a 40GB Hard drive, at least 256MB of RAM.  With antivirus and spam you might want to consider 512 to 1GB.  

Have you taken a look at [OpenXChange]("http://mirror.open-xchange.org/ox/EN/community/")?  It looks like it may be able to handle all of your needs without the headaches.

---

### Post by el3ktro on 2006-04-26
I was thinking about something like this:

[https://www.server4you.de/de/d/index.html](https://www.server4you.de/de/d/index.html)

(scroll down, on the left there's a server called "RootPower"), it's in German but you should get the point ;-)

Do you think such a thing would be powerful enough?

Another question: I was just thinking that when this server runs for months, years ... all the emails would take up more and more space. So I had the following idea: All mails are saved in maildirs, so it _should_ be possible to let a cronjob run every month or so, which would tar all emails older than 3 years from all maildirs and move them to our in-house fileserver. This way, all really old (>3yrs) mails would be backed up, and all users would have all emails from the last 3 years available all time. IF ever a user needs a really old mail, I could just untar the appropiate tarball into the users' maildirs, because all maildir files are unique.

Tom

---

