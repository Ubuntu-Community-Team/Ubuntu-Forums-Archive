---
title: "Guess who's back?"
date: 2004-12-31
forum: Ubuntu Backports
---

### Post by jdong on 2004-12-31
Hey, guys, just got home 5 minutes ago, so backport work will be quick to begin.

However, this week or two will be very busy for me -- I got some last minute school deadlines to meet, plus exams coming up in 2 weeks. Backporting work will likely be slow for the 1st half of January.

---

### Post by senectus on 2005-01-01
Umm this may be a silly question.. but what exactly is the definition of a backport?

Is it bringing in to the warty repository, packages from the hoary repository?

or is it putting new apps into the warty repository?

---

### Post by jdong on 2005-01-01
I originally defined it as bringing Hoary and Sid packages to Warty. However, I'm getting a lot of requested packages that are in neither Hoary nor Sid, so I'll be opening up an 'extras' repository for that.

---

### Post by senectus on 2005-01-01
ok perhaps you can help explain to me what the deal is with rp-pppoe?
I'm trying to build an Ubuntu router/firewall and I'm using webmin to help make it simple..
one of the interesting things I've found is that the webmin-adsl module is in the repository, and when I install it and go to configure rp-pppoe (as webmin-pppoe is designed for rp-pppoe), the config files and bin for starting rp-pppoe are not there or in the wrong spots.
It seems that the rp-pppoe.so module is actually on the machine but thats it.. the rest appear to be a different adsl/pppoe application.

So is the Ubuntu package "pppoe" rp-pppoe or is it something else...?

---

### Post by fng on 2005-01-03
You need any developers helping you out with backports or extras?

---

