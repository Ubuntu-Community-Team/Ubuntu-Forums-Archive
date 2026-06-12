---
title: "ubuntu one options for nautilus are missing"
date: 2011-03-22
forum: Ubuntu One (CLOSED)
---

### Post by Stebbins on 2011-03-22
Ubuntu One wasn't syncing my files, so I tried reinstalling it.  Ubuntu One appears again in the Preferences tab, but the context sensitive menu options (for syncing/publishing) are completely gone from Nautilus.  What do I need to do to get these back?

I also deleted the Ubuntu One folder from my home directory.  Reinstalling Ubuntu One did not recreate it.  Can I recreate it manually?

Thanks for your help!

---

### Post by imblack on 2011-03-23
Try 'sudo apt-get purge ubuntuone'
Replace the ubuntuone with actual package name and then reinstall it, and then go to preferences and change the settings accordingly. Hope that helps

---

### Post by Stebbins on 2011-03-28
The issue resolved itself.  When the next automatic update occurred, Ubuntu completely reinstalled Ubuntu One.

---

