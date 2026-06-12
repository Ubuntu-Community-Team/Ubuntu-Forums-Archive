---
title: "Gdm_3.6.0 is broken"
date: 2012-09-26
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-09-26
Just installed the latest official QQ verison of Gdm (3.6.0).
I only have Gnome-shell and its fallback Gnome Classic installed on my QQ setup.
Also, I only have Gdm installed (no LightDM).

The version 3.5.92.1 works just fine, but the version 3.6.0 hangs and never opens the login window.
Downgrading to the previous version (3.5.92.1) solves the issue.

It may be due to this patch in the version 3.6.0:
* 09_default_session.patch:     - Dropped, all the other Ubuntu flavors use LightDM and it only       takes a gsettings override to set a different default session

---

### Post by Harry33 on 2012-09-27
The newest gnome-session_3.6.0 fixes this issue.

---

