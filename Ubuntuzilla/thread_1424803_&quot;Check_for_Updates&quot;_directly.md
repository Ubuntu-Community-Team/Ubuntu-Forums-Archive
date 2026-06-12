---
title: "&quot;Check for Updates&quot; directly?"
date: 2010-03-08
forum: Ubuntuzilla
---

### Post by Umang on 2010-03-08
Hi!
I noticed that the "Check For Updates" menu item under the Help menu is not disabled. I just wanted to know, since I've installed Firefox from the PPA, whether using this to upgrade Firefox would break anything.

---

### Post by nanotube on 2010-03-08
> **Umang said:**
> Hi!
I noticed that the "Check For Updates" menu item under the Help menu is not disabled. I just wanted to know, since I've installed Firefox from the PPA, whether using this to upgrade Firefox would break anything.

if you're running as regular user, you won't have permissions to actually install any updates you download with the built-in 'check for updates' function. 

You could 'gksudo firefox' then check for updates, and that should work. That said, it's probably cleaner to just pull the updates from the repo.

---

### Post by Umang on 2010-03-08
Thanks!

---

