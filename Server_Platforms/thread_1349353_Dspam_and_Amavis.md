---
title: "Dspam and Amavis"
date: 2009-12-08
forum: Server Platforms
---

### Post by coutts99 on 2009-12-08
Hi,

I am trying to integrate dspam with Amavis.

Everything looks good except I can't get Amavis to score the message according to the dspam headers.

I have the following in my local.cf -:

header DSPAM_SPAM X-DSPAM-Result =~ /Spam/
describe DSPAM_SPAM DSPAM claims it is spam
score DSPAM_SPAM 5.0

header DSPAM_HAM X-DSPAM-Result =~ /Innocent/
describe DSPAM_HAM DSPAM claims it is ham
score DSPAM_HAM -2.0


I can see the dspam headers in the emails, and amavis is checking the message, but those rules are not working.

Anyone any ideas why?

Cheers

---

### Post by coutts99 on 2009-12-08
Doh!

Restarting amavis helps :)

---

