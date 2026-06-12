---
title: "nicing amavisd (clamav and spamassassin)"
date: 2007-03-27
forum: Server Platforms
---

### Post by scottishnarn on 2007-03-27
I have a ubuntu 6.10 box serving as a mail server and mythtv box. It works fine for either of those two activities alone, but my mythtv playback get's jery if it's processing email. I think this down to amavisd-new (using clamav and spamassassin) rather than postfix it's self since I didn't used to get the problem on my old system (not ubuntu) which didn't run spam and virus checks. 

I know I can lower the priority of a program using nice but how do I apply this to a service, specifically amavisd-new, clamav and spamassassin.

(I set it up using the postfix, amavisd-new, clamav, spamassassin howto on the ubuntu wiki).

Thanks

---

### Post by Mr. C. on 2007-03-27
Amavis is being started by a script in /etc/init.d.  I don't know what you named it, so you'll have to find it there.  You can nice from there.

I'm a little bewildered at a combo mythtv box also running as an antivirus / antispam mailer.  Amavis and your MTA both have certain requirements on response times to avoid timeouts and/or dropped mail.  For example, set when amavis does not receive a response from spamassassin within a given time period, spam scanning is bypassed altogether.  The same can be true for A/V scanning.

MrC

---

