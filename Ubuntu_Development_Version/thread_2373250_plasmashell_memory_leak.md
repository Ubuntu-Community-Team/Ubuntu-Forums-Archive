---
title: "plasmashell memory leak"
date: 2017-10-04
forum: Ubuntu Development Version
---

### Post by loftwyr on 2017-10-04
Since upgrading  on Saturday, plasmashell has developed a terrible memory leak using over 32GB of memory/swap in 8 hours.  I've now got a cron job killing it ever 4 hours to stop the system from crawling to a halt.

I'm running the latest nvidia drivers from the graphicsdrivers ppa.

What can I do to figure out what's causing the leak?

---

### Post by loftwyr on 2017-10-05
Okay, process of elimination seems to have found the culprit.  I had 3 folder view widgets on my desktop.  

I did a complete reset of all plasma-workspace settings and then started adding widgets.  Once I added the folderviews the memory count started jumping.  Removed those again and restarted plasmashell and it's stable at 1% of memory

---

### Post by loftwyr on 2017-10-05
I was wrong, it was the slideshow background.  It's a known bug in QT.  A fixed background eliminated the problem once and for all even with the folderview widgets restored.

---

