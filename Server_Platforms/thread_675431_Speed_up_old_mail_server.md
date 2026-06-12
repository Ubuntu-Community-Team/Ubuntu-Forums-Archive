---
title: "Speed up old mail server"
date: 2008-01-22
forum: Server Platforms
---

### Post by quietas on 2008-01-22
Howdy folks. I have taken over as admin for what used to be a small network, thus they had a small mail server. It's a 2.0 P4 desktop computer with 2gb RAM (after upgrade last month,  running Debian 4 (it started as 3 till I upgraded recently), Exim, MailScanner, Spam Assassin, ClamAV, and Webmin. Along with those is runs Apache2, PHP4, and PHPGroupware for web access.

Essentially the company has grown from getting a couple hundred messages a day to several thousand. At this point the newer MailScanner is starting to overload the processor and at times mail delivery slows to a crawl.

Now what is the easiest way to speed up the mail delivery? I know and have plans for a new mail server, but upper VP's are slow to give me new toys.

Would it be possible to load balance between multiple servers, beowulf cluster, setup a separate spam/av scanning puter?

~ Culley

---

### Post by HermanAB on 2008-01-23
Add these RBLs: 
bl.spamcop.net
zen.spamhaus.org
dnsbl.ahbl.org

That should reduce the amount of incoming messages enormously.

Cheers,

Herman

---

### Post by MJN on 2008-01-23
You need to determine where your bottlenecks are - without doing so you are stabbing in the dark when it comes to speeding anything up.

If the delays are caused by spam-filtering that could be sidestepped altogether by blocking at the front door then as Herman suggests RBLs could help. However, there is a risk of losing legitimate mail by outright blocking with such lists if used in a pass/fail capacity - it is far more sensible to use the RBLs as part of a weighted scoring mechanism which you probably are doing anyway within SpamAssassin but this inevitably brings 'delay' (as opposed to load) which may, or may not, be a problem (a 10 second delay on every message is neither here nor there - it is a pipelined system hence nothing should be crawling).

Again, find out where the delays - measure everything - then work out where the bottlenecks are. You mentioned MailScanner is possibly being the culprit so check their mailing lists and other support channels to find out what's 'wrong'.

There is no reason why you should not process 10 times your current throughput on a machine of that spec hence if things really are crawling there probably is a significant configuration aspect that is responsible.

Mathew

---

