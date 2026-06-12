---
title: "[POSTFIX] Flurdy Guide and SpamAssassin Filters"
date: 2006-10-27
forum: Server Platforms
---

### Post by Kurdt on 2006-10-27
Hi

I am running a Postfix mail server set up with flurdy's guide using SpamAssassin as well with a Bayesian Filter.

At SpamAssasin site said this:

> If you want to set up site-wide use of Bayesian classification, you should set up a way for your users to send in misclassified mail to be "learned" from.

If you create mailboxes for false positives and false negatives, you can then run a cron job intermittently to learn all the mails in that mailbox as spam (or non-spam).


So i said to my users to send unwanted email to [email]trash@domain.com[/email] and [email]nonspam@domain.com[/email], currently i reached the number necessary to run the sa-learn filter and i saw this (at spamassasin site too):


> For MUAs (Like Netscape/Mozilla) that do a good job with keeping original headers intact, (almost) all you need to do is forward the email to the feedback account and strip off the header added by the forward.


1) Wich are exactly the headers added to an email in a forward situation?
2) Has someone gone throught this situation before? What did you do to clean the email from forward headers?

Thanks for all your help :)

---

