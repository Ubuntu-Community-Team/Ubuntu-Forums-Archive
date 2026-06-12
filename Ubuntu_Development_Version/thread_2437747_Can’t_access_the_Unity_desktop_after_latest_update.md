---
title: "Can’t access the Unity desktop after latest updates 20-02-27"
date: 2020-02-28
forum: Ubuntu Development Version
---

### Post by Yahoé on 2020-02-28
After yesterday’s updates 20-02-27, two of our Ubuntu Focal computers can’t access the Unity desktop any longer, only the Gnome session loads properly.
Upon successfully logging in Lightdm, the background image loads, the cursor is there, but that’s it, nothing else and no interaction whatsoever seems possible.

Is anyone else experiencing the same issue?

---

### Post by Yahoé on 2020-02-28
I ended up updating anything unity from proposed, and that fixed whatever got broken yesterday. The Unity desktop is loading again.

---

### Post by Chanath on 2020-02-29
Have a look here, [https://discourse.ubuntu.com/t/testing-unity-session-in-focal-fossa-20-04/13692/42](https://discourse.ubuntu.com/t/testing-unity-session-in-focal-fossa-20-04/13692/42)

---

### Post by Smask on 2020-02-29
No visible mouse pointer in the login/greeter screen and trying to start the Gnome Flashback desktop gives me the mouse pointer, background image and the desktop icons for a second. Then it's back to the login screen again. Unity still works.
Doh! I used gdm on this machine. Mouse pointer is back, still can't use Flashback.

---

### Post by muktupavels on 2020-03-02
Smask, check log files and report bug for GNOME Flashback.

---

