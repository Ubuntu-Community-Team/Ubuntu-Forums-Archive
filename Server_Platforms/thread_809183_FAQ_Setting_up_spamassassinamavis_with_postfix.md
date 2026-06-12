---
title: "FAQ: Setting up spamassassin/amavis with postfix"
date: 2008-05-27
forum: Server Platforms
---

### Post by supremedalek on 2008-05-27
This should be an easy question but is confusing the hell out of me. I have installed postfix with dovecot and set them up to handle two virtual domains, one with 5 users and another with 2. Now, I would like to deploy amavis and spamassassin but most of the information I am finding around assume my email users are also local users, which they obviously are not. Does anyone have any pointers for how-tos for deploying amavis + postfix with virtual domains?

---

### Post by gtdaqua on 2008-05-27
Try Zimbra - there is a free version which is quite easy to setup. Will help a lot if you are using Debian 4 or Ubuntu 6.06 server edition. You can setup multiple virtual domains and anti-spam/anti-virus comes built-in.

[Zimbra]("http://www.zimbra.com")

---

### Post by windependence on 2008-05-27
I'll second that, it's a great product.

-Tim

---

### Post by supremedalek on 2008-05-31
Thanks for the suggestion but I right now have a happy postfix+dovecot setup that only needs amavis to achieve nirvana. Scrambling that to Zimbra does not seem to be what I am really after. :)

---

