---
title: "Snort help"
date: 2010-12-10
forum: Security
---

### Post by bdemers on 2010-12-10
I realise all too well that I should be asking for newbie help in a Snort forum.  Believe me when I say that I've tried.  Would there, by any chance, be someone who might answer questions of a newbie level (like where do I define HOME_NET, that sort of question).  Perhaps off line, or in a more appropriate forum where ever that might be. Currently installing 2.9.0.2 in Ubuntu 10.04 server.  This has gone in a number of times already, successfully, but trying to get a grip on install options vs config options for yet another go-round.

---

### Post by bodhi.zazen on 2010-12-11
See the snort sticky for a walk through on snort

[http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696)

Otherwise if you have a specific question ....

---

### Post by bdemers on 2010-12-11
Thanks for the pointer, I just bookmarked that.  My initial questions regard the initial install, and the install options for 2.9.  I plan on eventually using this as an inline ips, not ids.  Can I just configure at make all the switches that are listed and use that one install as a sniffer, logger, etc? In other words use the same build in all 3 modes? I did a "find ./configure" in the user's manual, came up with a list of about 10 (+/-) switches, all but 2 seemed to be worthwhile to me, but not being close to an expert yet, don't really have a clue.  If I compile with all these switches, will I actually lose flexibility?  There seems to be some duplicity between the conf file and the startup switches, the startup switches taking priority, but I found nothing talking about the impact of the compile switches.

I also found nothing that relates to removal.  If I start in a sniff or log mode and it works out I need to rebuild for use as a ids or ips what do I do to change the app?  will I need to remove it or can I simply (ha) rebuild?

Is there a project out there that has a community more like ubuntu's?  Read that as helpful to the neophyte.  Maybe OISF? I am wondering about the wisdom in using a piece of software were its use is so closely held to the chest, almost cult-like. No wonder the bad guys win.  In my opinion, software is only as good as your ability to use it.  Ubuntu shows the way in that regards.  Sorry, end of rant!

---

### Post by bodhi.zazen on 2010-12-11
> **bdemers said:**
> Thanks for the pointer, I just bookmarked that.  My initial questions regard the initial install, and the install options for 2.9.  I plan on eventually using this as an inline ips, not ids.  Can I just configure at make all the switches that are listed and use that one install as a sniffer, logger, etc? In other words use the same build in all 3 modes? I did a "find ./configure" in the user's manual, came up with a list of about 10 (+/-) switches, all but 2 seemed to be worthwhile to me, but not being close to an expert yet, don't really have a clue.  If I compile with all these switches, will I actually lose flexibility?  There seems to be some duplicity between the conf file and the startup switches, the startup switches taking priority, but I found nothing talking about the impact of the compile switches.

I also found nothing that relates to removal.  If I start in a sniff or log mode and it works out I need to rebuild for use as a ids or ips what do I do to change the app?  will I need to remove it or can I simply (ha) rebuild?

Is there a project out there that has a community more like ubuntu's?  Read that as helpful to the neophyte.  Maybe OISF? I am wondering about the wisdom in using a piece of software were its use is so closely held to the chest, almost cult-like. No wonder the bad guys win.  In my opinion, software is only as good as your ability to use it.  Ubuntu shows the way in that regards.  Sorry, end of rant!

Personally I would not use snort in this way, take a look at psad and fwsnort.

[http://bodhizazen.net/Tutorials/psad/](http://bodhizazen.net/Tutorials/psad/)

Otherwise, google search for snort inline

---

### Post by bdemers on 2010-12-11
Hmmm, so by using psad with fwsnort, I can get the eq of snort running inline since the rules are being converted to iptable entries.  To decide on what rules to use I could set up a sniffer/logger/ids system (snort for this?), discover my positives and fill in with whatever iptable entries I need.  This about right?

I did notice a reference to a couple of available patch files for 2.4 only.  This implying I should stay with a 2.4 distribution?

This is great, you are giving me wonderful option here

---

### Post by bodhi.zazen on 2010-12-11
fwsnort analyzes you iptables rules, and adds rules only for open ports, so it is much more efficient. If you are adding hundreds of rules with fwsnort, tighten your iptables rule set.

---

