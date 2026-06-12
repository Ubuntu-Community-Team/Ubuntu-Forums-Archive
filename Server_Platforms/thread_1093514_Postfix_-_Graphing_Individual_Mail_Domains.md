---
title: "Postfix - Graphing Individual Mail Domains"
date: 2009-03-11
forum: Server Platforms
---

### Post by wdaly on 2009-03-11
Hi,
Run 70+ Virtual Domains in POSTFIX 
Postfix logs to /var/log/mail.log
Would like to see graphs & stats separately for each domain. 

I have been attempting to use [Awstats with included maillogconvert.pl script. ]("http://awstats.sourceforge.net/docs/awstats_faq.html#MAIL")
Since I use amavisd-new I first process the mail.log with [prepflog.pl ]("http://web.tiscali.it/postfix/prepflog.html")

The Awstats,prepflog,Maillogconvert seems promising, but it's not playing nice. It's generating the same statics for every Domain. As you can see it only mentions virtual domains with VAdmin QMail. 

Has anyone experience with running multiple domains in Postfix and generating separate graphs and statistics for each domain. (so that owners of each domain can view just their email graphs & stats)

Anyone interested in graphing their Postfix traffic including SPAM check out [mailgraph ]("http://mailgraph.schweikert.ch/")
This is really good, but would be nice if it would work per domain.

I have checked Freshmeat, Sourceforge .. there seems to be lots of graphing programs, just not many that handle postfix logs with virtual domains and then graph. 

Any ideas welcome. Thanks so much. 
Warren 

Ubuntu Server X64 6.06 
Postfix 2.2.10

---

### Post by lucaspr on 2009-10-07
Thanx for your message. Mailgraph was exactly what I needed!

---

