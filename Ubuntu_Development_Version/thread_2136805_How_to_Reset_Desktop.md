---
title: "How to Reset Desktop?"
date: 2013-04-18
forum: Ubuntu Development Version
---

### Post by ping-wu on 2013-04-18
How to reset desktop?  I mean resetting the entire desktop, including the menu (?) bar at the top right of the screen?

---

### Post by ajgreeny on 2013-04-18
Which version of *ubuntu?

Sorry!  Just noticed it is 13.04, so I can't help you.

---

### Post by Hreinsi on 2013-04-18
setsid unity

---

### Post by Hreinsi on 2013-04-18
for compiz reset: Install dconf-tools
dconf reset -f /org/compiz/   log out and in.
To refresh your Unity launcher with the default set of icons:   unity --reset-icons

---

### Post by philinux on 2013-04-19
> **Hreinsi said:**
> for compiz reset: Install dconf-tools
dconf reset -f /org/compiz/   log out and in.
To refresh your Unity launcher with the default set of icons:   unity --reset-icons

No need to log out and back in. Following dconf reset -f /org/compiz/ just use setsid unity which will restart unity.

This dconf bit will reset unity.

---

