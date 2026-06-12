---
title: "Postfix configuration"
date: 2007-06-09
forum: Server Platforms
---

### Post by Luft on 2007-06-09
How do I configure my Postfix mail server to send and receive email from my Comcast account?  I'm setting up a Drupal site and I need the site to be able to email people their passwords etc...  But Comcast blocks home mail servers which is fine.  I just need to use my Comcast account to send and received via my mail server.

Thanks

---

### Post by hawzor on 2007-06-11
Hi Luft,

You have a problem similar to one that we have...we send routinely mail to our clients too.

However, I am not sure this is a Postfix issue (I may be wrong), but more of a Comcast issue.

If they are similar to Earthlink and Cox aso, you would generally need to relay through their SMTP servers, ***AND ***do so from within their network to avoid problems. This is their weak/lame attempt to control spam. Try to relay through their SMTP from outside and yours already are denied/dropped.

One weak/lame workaround we have done is created a Reply-To account, added that line in the outgoing mail headers (PHP) and then actually manned that account to perform their anti-spam C/R (challenge response) mailers that bounce back and test for human listener, which then lets the message through, but with some overhead on our part and some delay to the user. If a user signs up at 2:00 AM PST, they may not get their password until 9:30, hours later. As I am saying already: weaksauce.

Did I understand your issue?

HK

---

