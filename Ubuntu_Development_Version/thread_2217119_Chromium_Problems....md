---
title: "Chromium Problems..."
date: 2014-04-15
forum: Ubuntu Development Version
---

### Post by TenPlus1 on 2014-04-15
So I updated Lubuntu 14.04 today and got a new version of Chromium to play with...  Once I go to a webpage the keyboard no longer lets me enter anything into the browser, and the flash plugin isn't recognised anymore and I had to install pepper flash from the repo's to get flash working again (which doesn't do hardware acceleration)...

Anyone else having same problems ??

---

### Post by bapoumba on 2014-04-15
Not here, which flavor of ubuntu are you running on which hardware ?

---

### Post by TenPlus1 on 2014-04-16
I'm running the latest daily of Lubuntu 14.04 but it does the same thing on Xubuntu as well...  Chromium 33 worked perfectly it's juse since the v34 update that problems are starting to arise, and I cannot force a previous version for this package...

Acer Aspire Revo 1.8 Dual Core with 2GB memory, Nvidia Ion.v2 gfx and 120GB SSD drive...

---

### Post by ronb19495 on 2014-04-16
I have google chrome 34 running on ubuntu unity today it wouldnt find anything from the middle search box some how it fixed itself firefox was doing the same. firefox still doing same not searching from centre search box,Ijust cleared history and cache now its working ok again.

---

### Post by TenPlus1 on 2014-04-17
This explains a lot: [http://www.phoronix.com/scan.php?page=news_item&px=MTY2NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTY2NTg) (chromium moving from gtk2 to aura and removing npapi plugins)...  It may be that my nvidia binary drivers are not helping as having the noveau open-source one's running let me enter text normally inside chromium...

---

### Post by ronb19495 on 2014-04-17
I just installed google chrome beta and it appears to be working fine on 14.04

---

### Post by bapoumba on 2014-04-17
> **ronb19495 said:**
> I just installed google chrome beta and it appears to be working fine on 14.04

Good to know, thanks, will test it out as Chromium has the same behaviour re: flash here as described in this thread.

---

### Post by TenPlus1 on 2014-04-22
Turns out ibus was causing problems with text input for Chromium so I've uninstalled the ibus package and restarted to find that Chromium once again works ok with the keyboard...

---

### Post by bapoumba on 2014-04-22
Glad to see you got it to work. Would you please mark your thread as Solved (in Thread Tools), thanks :)

---

