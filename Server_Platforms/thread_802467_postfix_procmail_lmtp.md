---
title: "postfix procmail lmtp"
date: 2008-05-21
forum: Server Platforms
---

### Post by cdenley on 2008-05-21
I'm setting up a Citadel mail server. I wanted to have spam mail go into a seperate folder, instead of it being dropped.

[http://www.citadel.org/doku.php/faq:spam:spamassassin#configuring.a.per.user.spam.folder](http://www.citadel.org/doku.php/faq:spam:spamassassin#configuring.a.per.user.spam.folder)

So I install postfix and procmail. It works perfectly, except procmail is never used. It will flag it as spam, but it still goes to the inbox. It seems that whichever command I set for mailbox_command in /etc/postfix/main.cf never gets run. Is this because I'm using LMTP? Is there another way I can go about this?

I can't get the sieve filter to work for x-spam-flag, either.

---

