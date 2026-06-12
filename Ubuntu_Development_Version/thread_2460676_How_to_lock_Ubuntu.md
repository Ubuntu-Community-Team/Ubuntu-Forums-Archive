---
title: "How to lock Ubuntu"
date: 2021-04-15
forum: Ubuntu Development Version
---

### Post by yaminb on 2021-04-15
Perhaps a really silly question, but how do I lock my workstation?
Not turn the screen off. Not go to sleep. Just lock it.

I see the option in settings and I've set the key combination (Super + L). I've also tried others. Nothing seems to work.
There isn't an option in the menu (only logout and power.

I did recently upgrade to 21.04 beta. i don't think that has anything to do with it, but who knows.

---

### Post by jeremy31 on 2021-04-16
Moved to Ubuntu Dev version as 21.04 hasn't been released

---

### Post by mikewhatever on 2021-04-16
You buy an iron box with a lock, put the workstation in, and lock the lock. Simple!

---

### Post by zebra2 on 2021-04-16
My [Window key] + [L] locks the computer (21.04). I also have a Lock option with the Power OFF link it the upper right corner. They both work but until I know what their limitations are I'm going with mikewhatever and the iron box. Is your disk encrypted?

PS and that goes for my Windows partition that locks exactly the same way.

---

### Post by yaminb on 2021-04-16
hmmm. Are there any configuration files that typically control locking? I have no idea where to start looking to how to fix this.

---

### Post by yaminb on 2021-04-16
Solved it.
For some unknown reason this was set to true.
gsettings get org.gnome.desktop.lockdown disable-lock-screen

To fix it, 

gsettings set org.gnome.desktop.lockdown disable-lock-screen false

---

