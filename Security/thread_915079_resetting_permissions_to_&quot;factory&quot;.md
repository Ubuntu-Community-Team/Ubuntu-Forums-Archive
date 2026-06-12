---
title: "resetting permissions to &quot;factory&quot;"
date: 2008-09-09
forum: Security
---

### Post by anystupidname on 2008-09-09
I have since reinstalled completely to fix this problem but I still have a question. In short, I screwed up permissions pretty badly having confused one mount point with another and chmoding it (at least I THINK that is what happened) which resulted in me not being able to sudo anything or even su. I found a particular post [http://ubuntuforums.org/archive/index.php/t-219767.html]("http://ubuntuforums.org/archive/index.php/t-219767.html") on here which described the problem I was having partially but the suggested solutions that worked for some didn't work for me (namely, booting with rescue CD, mounting file system, and changing permissions on /usr/ or /usr/bin/sudo or something like that) because of an error "refused uid 999". My question is, if I were to ever screw up permissions in a way I couldn't comprehend AGAIN, is there a simple way to just force all permissions back to "factory" or virgin install state? Thanks for any input on this!

---

### Post by HermanAB on 2008-09-09
Yes, there is.  You boot from the install CD and re-install the system.  That will take about 30 minutes.  Your user data will be unaffected if you DON'T reformat the /home directory.  However, if you have data in other places or if you don't have separate partitions, then you have to first backup your data.

...and this is why you should always have a separate /home directory...

---

### Post by anystupidname on 2008-09-10
> **HermanAB said:**
> Yes, there is.  You boot from the install CD and re-install the system.  That will take about 30 minutes.  Your user data will be unaffected if you DON'T reformat the /home directory.  However, if you have data in other places or if you don't have separate partitions, then you have to first backup your data.

...and this is why you should always have a separate /home directory...

Yea, as I stated, I was aware of the option to reinstall. Which I used. I was asking for OTHER possibilities. If it was just the 30 minutes, I'd be OK with re-installing each time. But we're talking about 30 minutes of near constant baby sitting. And with the problem described [here]("http://ubuntuforums.org/showthread.php?t=915293"), it is way over 30 minutes anyway...

---

