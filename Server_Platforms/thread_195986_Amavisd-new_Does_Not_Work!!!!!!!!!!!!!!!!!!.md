---
title: "Amavisd-new Does Not Work!!!!!!!!!!!!!!!!!!"
date: 2006-06-13
forum: Server Platforms
---

### Post by dwscholl on 2006-06-13
Cannot get amavisd-new to tag mail headers for spam or scan for viruses with clamd. I have set up several spam filter gateways on Debian stable with no problems. However amavisd-new on dapper does not work. I have succesfully configured postfix to pass mail through amavis and onto the exchange server, but no messages are being taged for spam. 

Also mail.err log says WARN: all primary virus scanners failed. clamscan then runs and tags the header as being scanned for viruses, but spamd/spamassassin does nothing. Have set default tag level to -1.0. No header tags please help!!!!

And who got the idea to go to the conf.d directory?!! Yes, amavis.conf is large and hard to work with but it woks!!!!!

Wish I had stayed with Debian stable or testing.

Sory for the rant.

---

