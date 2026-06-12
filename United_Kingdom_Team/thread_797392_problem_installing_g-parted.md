---
title: "problem installing g-parted"
date: 2008-05-17
forum: United Kingdom Team
---

### Post by mikeocaiside on 2008-05-17
I tried installing g-parted on my IBM THINKPAD X23 running ubuntu 8.04 using package manager from online depository, but it has not finished installing fully and now my hard drive is being read all the time even when laptop is idle.

G-Parted does not show in accessories but shows as installed under package manager. I have tried uninstalling and reinstalling but is still the same situation.

Can anybody help as I am a newbie

Mike

---

### Post by ajgreeny on 2008-05-17
You could try using synaptic and "Fix Broken Packages" in the edit menu, but if that doesn't work try entering ```
sudo dpkg --configure -a
```in terminal.  That may well fix it for you.

---

### Post by redoscar3 on 2008-05-17
You might try running:

> sudo dpkg-reconfigure gparted

to see if that clears up your problem.  Or completely uninstall and reinstall the package.

Red

---

