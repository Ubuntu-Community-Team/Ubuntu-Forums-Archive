---
title: "Apparmor and Firefox"
date: 2009-04-06
forum: Security
---

### Post by Thelasko on 2009-04-06
So, every time there's an update for Firefox I have to update my AppArmor profile manually?  Is there a way around this?

---

### Post by bodhi.zazen on 2009-04-06
You do not need to re-create the profile, just edit the profile and add in the new version number.

This behavior has been reported as a bug, although I do not know the status.

---

### Post by Thelasko on 2009-04-06
Thanks!

---

### Post by jdong on 2009-04-07
Yeah, the fundamental problem is that applications to not consistently launch "/usr/bin/firefox" or "/usr/lib/firefox-3.0.x/firefox".... If you set the profile in /usr/bin/firefox, a direct invocation of the /lib version will bypass AppArmor.

---

