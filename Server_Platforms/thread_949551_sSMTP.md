---
title: "sSMTP"
date: 2008-10-16
forum: Server Platforms
---

### Post by ginbas on 2008-10-16
Hey guys,

I'm attempting to use sSMTP to forward system mail to a Gmail account. Everything is working correctly accept that I can not get ssmtp to forward or alias "root" mail to the Gmail address.

This should be a simple task and configuration within ssmtp but its just not working. 

I know of the limitations of ssmtp but this is exactly what I need.

The system is running 7.04

Regards,
Gin

---

### Post by Nostalos on 2008-10-16
Have this configured myself.   Take a look at the Gentoo Wiki on how to set this up.

[http://gentoo-wiki.com/HOWTO_Gmail_and_sSMTP](http://gentoo-wiki.com/HOWTO_Gmail_and_sSMTP)

Take special note on sending emails to/from the same address.  If you are sending emails to yourself through the same account they will only show up in your sent box.   I had to set up a seperate account for root in order to receive logwatch emails to my personal account.

---

### Post by ginbas on 2008-10-17
Thanks Nostalos. Unfortunetly, I have been all through the various install guides. For some reason, the process is totally ignoring the "revaliases" file.

For now I've specifided the MAILTO=hostname@provider.com in the crontab for the process I need the output of so it's a work around for now.

---

