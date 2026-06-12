---
title: "Citadel working on 12.04?"
date: 2012-05-19
forum: Server Platforms
---

### Post by moonpup on 2012-05-19
I just setup a 12.04 server and wanted to test Citadel. I went through the install and configuration menus taking the defaults, but it fails to start and errors in /var/log/syslog talk about doing a DB_recovery.

Does this not work out of the box anymore like it did on 10.04?

---

### Post by moonpup on 2012-05-22
bump... anyone?

---

### Post by artcancro on 2012-06-26
> **moonpup said:**
> I just setup a 12.04 server and wanted to test Citadel. I went through the install and configuration menus taking the defaults, but it fails to start and errors in /var/log/syslog talk about doing a DB_recovery.

Does this not work out of the box anymore like it did on 10.04?

Are you using the Easy Install method?  A couple of people had reported problems with 12.04 mainly due to problems with the version of libcurl that Easy Install ships; that version of libcurl is problematic on 12.04 (not just with Citadel, either).

The good news is that Easy Install now uses a version of libcurl that is happy on 12.04, so you should be able to update Citadel now with no problem.

As always, take a good backup before any major upgrade.

---

### Post by pmla on 2012-06-27
lol...
**Citadel email server or MTA is nightmare**... use at your own risk and be prepared for constant berkley database meltdowns. You will get accustomed to loose all your emails, contacts, calendars, settings, etc,  every month :) ... as you could already see, also check their joke bbs non-support :) more grunting and blaming you.

Used it at work for 2 months, big mistake :) worse time of my life :)
Used it for months at home until 2 days ago. Their "easy update" melted down my ubuntu 12.04 server... it was easy alright
Their ubuntu repositories are also a joke full of bad coding that needs to be constantly replaced.

Basically, the truth about citadel ... and please check their support forum :) ... although they have been cleaning the forum of not so good messages ;)
- old style bbs grunts, no support, it usually breaks because of their errors.... but according to them, it's your fault :) and then they might point you to some local wiki page with useless info.
- Pre-historic, slow, meltdown every month berkely database... not mysql, or sqlite3... no, no berkeley
- Most of the stuff does not work as publicize, please test it yourself, sieve rule to forward emails, calendars, upload a logo, etc, etc, etc.
- Calendar, yes, used it for 2 days, then it mysteriously deleted all my entries... so during this time I was using google calendar 
- old webmail GUI page, but they are very proud of it
- Administrator GUI page, useless... most of the commands need to be issue with bbs command line.
- Rooms instead of distribution lists? makes sense in their bbs head :)
- The list could go on with grouping rooms to assign rules, high cpu and memory process usage, specially with webcit... and yes, website crashes too.

What you should do:
Zimbra Open Source Edition ...wow Ôô it's light years ahead, very easy install and afterwards everything can be done using the administrator web gui, apache and ajax based.
here's the install how-to:
[http://www.zimbra.com/forums/installation/56367-my-notes-installing-zimbra-ose-ubuntu-server-10-04-lts.html]("http://www.zimbra.com/forums/installation/56367-my-notes-installing-zimbra-ose-ubuntu-server-10-04-lts.html")
In my case, I started in post n.5 and it was very easy.

---

