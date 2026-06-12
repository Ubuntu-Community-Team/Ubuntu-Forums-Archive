---
title: "Firefox not starting from launcher (starts fine from terminal)"
date: 2023-03-28
forum: Ubuntu Development Version
---

### Post by Wise Ferret on 2023-03-28
Using ubuntu with x11 session, nvidia proprietary drivers.
For a while now, firefox does not launch when I click it's icon on the launcher. I get the "thinking" cursor for a while, and that's it.
It starts fine from terminal or from alt+f2 prompt.
Any ideas? What should I look for?

---

### Post by corradoventu on 2023-03-28
Wait for these bugs:
[https://bugzilla.mozilla.org/show_bug.cgi?id=1824077](https://bugzilla.mozilla.org/show_bug.cgi?id=1824077)
[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/2011806](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/2011806) ... just fixed ... after update+upgrade requires a restart

---

### Post by SeijiSensei on 2023-03-28
Right click on the icon and examine its properties. Make sure it is pointing to the right executable.

---

### Post by Wise Ferret on 2023-03-28
Fixed with last gnome-shell update. Thanks all!

---

