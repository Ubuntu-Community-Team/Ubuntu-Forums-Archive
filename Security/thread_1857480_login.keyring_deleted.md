---
title: "login.keyring deleted"
date: 2011-10-10
forum: Security
---

### Post by pitomir on 2011-10-10
I have deleted login.keyring by mistake and restarted the computer. And now I can't log in! What can I do? ](*,)

---

### Post by raja.genupula on 2011-10-12
Hi, go to recovery mode from Grub menu and then to root shell then do this.

```
sudo apt-get remove libpam-gnome-keyring
```

```
sudo apt-get install libpam-gnome-keyring ubuntu-desktop
```

all the best.
Let me know if you got any.

---

### Post by rollin77 on 2011-10-18
I did the exact same thing and am having the same problem.  Clicking on either of the 2 user accounts I have setup gives me an error saying:
"error initializing conversation with authentication system - general failure"

I can't even enter my password or anything.

I  tried the above steps to no avail, (tried it twice just to be sure).  Still getting the same error.

I'm about to throw this laptop at my wall

What else can I try?

---

