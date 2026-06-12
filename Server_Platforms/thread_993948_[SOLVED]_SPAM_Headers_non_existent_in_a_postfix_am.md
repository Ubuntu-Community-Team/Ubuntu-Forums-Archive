---
title: "[SOLVED] SPAM Headers non existent in a postfix amavisd spamassassin setting..."
date: 2008-11-26
forum: Server Platforms
---

### Post by dulbirakan on 2008-11-26
Hi to all of you, o ever so helpful linux people.

I am trying to set a mail server straight, but I fail with spamassassin.

I try to set up a postfix amavisd clamav spamassassin dovecot server on a 8.10 ubuntu server. All looks fine except I see no spam headers in mails...

What I see is a X-Virus Scanned flag but no spam flags...

Any suggestions?

---

### Post by dulbirakan on 2008-11-27
Yep, now I found it... I was testing with the hostname from outside and the host name did not match the domain name. So amavis thought the mail was not for itself and did not perform the spamcheck. When I send the mail with the domain name as suffix, it is checked alright.

I mean when I used gmail to send mail to myself I had to use [email]dulbirakan@newbirakan.birak.com[/email] .

But amavis had local maps sert to birak.com so it did not check the mail against spam...

When I sent the mail from and internal account like [email]birakya@birak.com[/email] to another like [email]dul@birak.com[/email], it was solved. All checks were performed and the spam headers were in place.

I would thank me if I could.

---

