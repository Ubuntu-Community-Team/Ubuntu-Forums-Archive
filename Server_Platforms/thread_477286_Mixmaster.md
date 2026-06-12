---
title: "Mixmaster"
date: 2007-06-18
forum: Server Platforms
---

### Post by deadlinx on 2007-06-18
Hi,

I've installed Mixmaster via apt-get which seems not to be a stable release.

I've modified the config file to point sendmail in the directory where it lies
(/usr/sbin instead of /usr/bin).

I found the mix.cfg if not necessary and we can directly edit files in /etc/mixmaster/

I read the documentation, so I followed the instructions for choosing 
a reliable remailer chain and so on, but when I send mails always seems 
to go in the right way ("Sending messages...", "Done") and I've no error output 
but in the end I've no new messages in my inbox.


I can't find error output and the use of Mixmaster is easy (few steps) so is there anyone 
able to get a solution about it?


Maybe the problem is the deb package is not a stable, so maybe I'd remove it and build it from stable from source.


Sincerely

deadlinx

---

### Post by Adnarim on 2007-07-19
The same problem here but I got a bit further than you ;) The problem has nothing to do with mixmaster, as you said there's no error with mixmaster when sending mails but the problem has to do with sendmail/postfix. It is not configured by default by Ubuntu so you can't send mails with it. And if you can't send mails with sendmail, mixmaster also can't.

But could someone be so gentile and explain how to setup sendmail/postfix correctly for using mixmaster because I'm a bit scarred of ending up with an open smtp-relay which could be abused for spamming... How to prevent this? I want sendmail just to be useable by localhost and just use it with mixmaster. I've no other need for it.

greets

---

