---
title: "Is it applying change at instaling wine take time so long at point 85%?"
date: 2010-06-03
forum: Wine
---

### Post by rudysuryanto on 2010-06-03
Dear all, I try to install wine in ubuntu 10.04, I look process installing wine first step is downloading then applying change, in my computer applying change take time so long, approximately need 30 minutes, especially at point 85% and it is has not been finished yet, then I decide to hibernate my computer, is the installation of wine can be fail if I hibernate computer then continue again when I turn on my computer?Thank's.

---

### Post by cogadh on 2010-06-03
Yes, the install will most likely fail if you hibernate and resume in the middle of it. However, it shouldn't take so long to install, so there is probably something wrong with the installation already. I would reboot, then try the install again. If it still fails, open a terminal and run "sudo apt-get repair" to try to fix the issue.

---

