---
title: "Alt + left mouse button to move/drag windows not working"
date: 2012-08-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-08-14
I normally move windows by holding left-alt, pressing the left mouse button anywhere in the target window and moving the mouse. It's not working anymore for me.

I have just realized it, so I can't associate with a group of updates :\

Anyone confirm?

Regards,
Effenberg

---

### Post by mc4man on 2012-08-14
Just did a fresh install last night (main user account had irreversible issues), works fine here
Can you left click on window deco & move?

(ot - there is a new compiz crasher here, but already as private..

---

### Post by effenberg0x0 on 2012-08-14
> **mc4man said:**
> Just did a fresh install last night (main user account had irreversible issues), works fine here
Can you left click on window deco & move?

(ot - there is a new compiz crasher here, but already as private..

Yep, windows move normally if I just grab their title bar, with or without left-alt. I just double-checked PPAs and sources.list (all standard) and sudo apt-get update/upgrade again, restarted, and it persists.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-08-14
It has something to do with chromium! I killed (ps | grep chrom) pids and left-alt + left mouse button started moving windows again as expected.

Regards,
Effenberg

---

### Post by hpuri on 2012-08-25
Maybe because Googletalk plugin is doing something funny with the left mouse button ?

In firefox, the google talk plugin disables the left mouse button completely. you have to log out and log back in for the left mouse button to work again.

---

