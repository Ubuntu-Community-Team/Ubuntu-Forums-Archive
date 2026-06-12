---
title: "Postfix as internal mail server only"
date: 2010-03-08
forum: Server Platforms
---

### Post by strixx on 2010-03-08
Hi,

I want to setup Postfix on my Ubuntu 8.04 server acting as a local mail server only. I don't have my on domain. Is that possible and how do I do it?

I have googled it for several days without finding the answer.

The reason for installing postfix is that I want to set up Zarafa on my server acting as a mail/calender server, and then i will sync all my computers/smartphones with it.

Then I will use the "relayhost" option to relay all outgoing mail to me ISPs SMTP server, and I will use Fetchmail to poll incoming mail.

---

### Post by strixx on 2010-03-08
Found it my self! :D

[http://www.postfix.org/SOHO_README.html#fantasy](http://www.postfix.org/SOHO_README.html#fantasy)

---

