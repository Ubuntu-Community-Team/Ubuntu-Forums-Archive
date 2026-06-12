---
title: "two terms open and no pass check"
date: 2009-08-07
forum: Security
---

### Post by nomkev on 2009-08-07
ok, so i searched for this and couldnt find anthing about it.

i have a perl script, permissions are root only, and i have been running it from a launcher on the panel.

on startup, the launchers terminal OR running it manually from a normal terminal ask me for the root pass. this is fine. after entering the pass and finishing my business, i can close either, sudo -k or -K, and upon opening again, both will ask me for my pass again. this is also fine. HOWEVER, if i then open a new terminal and then hit the launcher while the new terminal is open, no pass is required in the launcher window. ive tried various combinations, and this is happening every time; individually theyre protected, but together, not.

any ideas?
nomkev

---

### Post by wojox on 2009-08-07
After the HOWEVER part do you invoke the script and then click the launcher?

---

### Post by nomkev on 2009-08-07
> **wojox said:**
> After the HOWEVER part do you invoke the script and then click the launcher?

i open the new terminal, dont touch a thing, and then hit the launcher.
ive been playing with this for hours but it seems to be the case.

---

