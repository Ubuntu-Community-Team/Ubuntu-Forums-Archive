---
title: "network monitoring tool"
date: 2007-01-16
forum: Server Platforms
---

### Post by Ivan Perzan on 2007-01-16
Hi, using 6.06LTS as file and mail server but would like to install on it some network monitoring tool. Currently there is PRTG installed on my windows machine where I can check bandwidth usage on 3 pc in our office network (primary to see who is using P2P during work hours:) ). But as its a demo cannot set all 7 of them :S. Any suggestion what app would be nice?

---

### Post by earobinson on 2007-01-16
ethereal is a great one, but the project has been renamed to wireshark, pretty sure its still ethereal in the ubuntu repos though

---

### Post by Brazen on 2007-01-16
[MRTG]("http://oss.oetiker.ch/mrtg/") might work for you.

I believe Ethereal just does local traffic.

---

### Post by GrammatonCleric on 2007-01-16
Look at [Cacti ]("http://cacti.net/")and [Nagios]("http://nagios.org/").  Both are in the repos not to mention Cacti is FAR easier to setup then MTRG.

---

