---
title: "ESMTP broken pipe"
date: 2008-01-22
forum: Server Platforms
---

### Post by pofigster on 2008-01-22
Howdy!

So, I posted earlier today about getting some kind of MTA installed on my server so that my PHP scripts can use the mail() function (and have it actually work).

I had a suggestion to use nullmailer - I tried it, didn't really work.  Then I saw a related post talking about how amazing ESMTP is.  I installed it, the configuration file is a cinch - and then, when I try to use the command sendmail or esmtp (with a destination address) I get an error back complaining that the SMTP server couldn't be resolved (yes, I am connected to the internet) and then on the next like complains about a broken pipe.

Any ideas on what could be causing this?  Or any pointers on getting nullmailer set up properly?  Thanks!

---

