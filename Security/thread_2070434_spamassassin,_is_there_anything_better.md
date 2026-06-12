---
title: "spamassassin, is there anything better?"
date: 2012-10-12
forum: Security
---

### Post by gertcher on 2012-10-12
I am just getting to grips with Ubuntu, for the 3rd time in the same years

It seems spamassassin is the default spam filter. I have been looking for reviews about it without success. I find it strange I cannot find reviews, after all spamassasin has been around a long time.

Just because something is the default does not mean it is the best. My question is, is there any other spam filter as good or better and easier to use?

Thanks  Greg

---

### Post by claracc on 2012-10-13
I use bogofilter as spam filter in evolution.

---

### Post by HermanAB on 2012-10-14
Howdy,

Spamassassin is a community driven thing and since it has the biggest community, it works the best.

You could DIY with Bogofilter, SpamBayes etc, but the most important thing is to use a DNS black list on your mail server such as Spamcop and Spamhaus, since those two will drop 99.999% of the cruft with almost no overhead.

---

### Post by lisati on 2012-10-14
Just to clarify, are we talking about a setup where you're using an email client (e.g. Evolution, Thunderbird, etc.) only, or are you running your own email server? 

Either way, you might find that a combination of techniques works better than one system on its own.

I use a combination of spamassassin/clamav/amavis-new, DNSBL checks and some custom-written policy & content filters for my email server. The end result is that the spam isn't rejected outright usually has some clear indication in the subject line and/or headers.

---

### Post by gertcher on 2012-10-14
Thanks for your input.

I am running Thunderbird.  As spamassassin is loaded through Thunderbird it gives that little extra reassurance it is virus clean. As you say it is well supported, therefore should be very good. This is the route I will take.

I am also going to use Calm, read about it in Computer Shopper (UK) today

Thanks  Greg

---

