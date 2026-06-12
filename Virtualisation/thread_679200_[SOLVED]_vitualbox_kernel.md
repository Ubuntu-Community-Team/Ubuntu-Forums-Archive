---
title: "[SOLVED] vitualbox kernel"
date: 2008-01-26
forum: Virtualisation
---

### Post by famous3warriors on 2008-01-26
I am trying to get virtual box to work and this is the error I get when I hit the start button.  Virtualbox kernel driver is not accessible to the current user.  How do I go about fixing that.  Thanks for your help.  :guitar:

---

### Post by p_quarles on 2008-01-26
You need to add your user to "vboxusers" group. Open a terminal, and run the following command:
```
sudo useradd *yourname* vboxusers
```
Once you've done that, you need to log out of the current session, then log back in. If everything else is configured correctly, Virtualbox will now work for you.

---

### Post by sumguy231 on 2008-01-26
Use the users and groups tool to see if your user is in the 'vboxusers' group. If that doesn't work, then how did you install Virtualbox?

Edit: Beaten.

---

### Post by famous3warriors on 2008-01-27
that guys for you help.  i really do appreciate the time to help I forgot to mark the thread as solved.  I did do the sudo useradd yourname vboxusers and it worked great.  Thanks once again.

---

