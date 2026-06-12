---
title: "evolution issue after upgrading to xubuntu beta 1"
date: 2014-08-30
forum: Ubuntu Development Version
---

### Post by justausr2 on 2014-08-30
I upgraded to  utpoic beta 1 on xubuntu.  After I upgraded I tried to run evolution.  If I do a ps I can see it is running, but no GUI.  I removed and reinstalled and same behavior.  Removed again and deleted everything in .cache/evolution and .config/evolution.  Then rebooted.  When I start I get the account setup dialogue.  I get through that but then no GUI but evolution is running.  I am creating an office365 account (EWS) but I had this before and all was fine.

Any ideas?

---

### Post by rapiertg on 2014-08-30
Confirm this behavior. Tried reinstalling, purging configuraton, but still can't see gui (however can see metting popups), and it seems evolution is running.

---

### Post by justausr2 on 2014-08-30
I tried a pop account and same behavior.  Tried uninstalling and setting ppa to the gnome3 staging but that didn't fix it.

---

### Post by justausr2 on 2014-09-04
Just tried again.  Removed all evolution, rebooted and installed but this time I didn't install evolution-ews.  I can add a pop account and evolution starts and I can get email.  I then install ews and when I start it hangs (even though now ews account is configured).  Remove ews and it runs again.  Guess we wait for the evolution folks to update/fix ews.

---

