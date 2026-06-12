---
title: "Logwatch customization"
date: 2007-01-22
forum: Server Platforms
---

### Post by DWStrauss on 2007-01-22
What is the preferred method of customizing Logwatch in Ubuntu releases?

I ask because I'm in the process of migrating my home server from FC2 (yes, you read that right) to Ubuntu 6.10 (Edgy) and I'm being overwhelmed by the amount of information Logwatch is sending me compared to the FC2 setup.  In particular, in the Postfix section of the daily report I'm getting one line in the "unmatched entries" subsection for each email the server delivers.  Since there are hundreds of these each day that's a lot of (mostly useless) information so wade through each morning.

I'm using Postfix as the MTA and Courier-imapd; Logwatch is version 7.3-1 installed with no modifications (so far).

Ideally I'd like to display only lines for emails that were delivered to unknown users (although how "unknown" gets defined is another story) but I would settle for just making all those unmatched entries go away.

Thanks.

 - Dave Strauss

---

### Post by DWStrauss on 2007-01-23
I've tracked down at least part of the issue: according to [this post]("http://www2.list.logwatch.org:81/pipermail/logwatch-devel/2006-August/001461.html"), Logwatch 7.3 is incompatible with Postfix 2.3.

Anyone know where I could find the patch?

---

### Post by DWStrauss on 2007-01-23
Here's what I did to fix the issue:  went to logwatch.org, clicked on the "CVS online" link, then scripts/ --> services/ --> postfix to look at the cvs log for the postfix script.  From the log, it seemed OK to try out the latest version (currently 1.28 ).  Clicked on 
"view", then "download", which opened a new window with the script source.  Cut and paste onto the local machine, then (as root) put a copy into /etc/logwatch/scripts/services (had to create the services directory).  Make the script executable (chmod 755 postfix), then run logwatch as a test:  logwatch --print > /tmp/logtest.  Look at /tmp/logtest to see everything is OK.

Is this the preferred method of overriding the installed scripts?  The downside I see to this is that I won't get any upgrades/changes to the postfix script.

---

### Post by Mr. C. on 2007-02-06
Dave,

I've extensively rewritten the postfix filter for logwatch, and am currently the official maintainer.

The latest postfix logwatch filter is at:

 [http://www.mikecappella.com/logwatch](http://www.mikecappella.com/logwatch)

A week-old version is also checked into the logwatch CVS repository.

Please download and unpackage the archive.  The README instructions there will guide you on next steps.

Send any questions or comments to the address listed in the README.

MrC

---

### Post by Mr. C. on 2007-02-13
The logwatch CVS repository now has the latest postfix filter (v1.30) for logwatch.

MrC

---

### Post by DWStrauss on 2007-02-13
Thanks!

---

