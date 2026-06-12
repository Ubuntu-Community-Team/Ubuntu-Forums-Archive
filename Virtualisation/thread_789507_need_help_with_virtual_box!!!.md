---
title: "need help with virtual box!!!"
date: 2008-05-10
forum: Virtualisation
---

### Post by mugen-R on 2008-05-10
i use ubuntu 8.04 and i wanna use virtual box but when i create tha virtual hard-drive and go to start the mashine to install (Xp for example) it says that i dont have the right to read or write to the virtual hd. So my question is how to make it work??? sorry for mistakes i'm greek and newby!!!thanks...

---

### Post by p_quarles on 2008-05-10
Moved to Virtualization. 

This is an easy-to-fix issue. You need to open a terminal emulator and add yourself to the group that "owns" Virtualbox:
```
sudo adduser *username* vboxusers
```
Following that, you'll just need to log out and then back in, so the group change can take effect.

---

### Post by mugen-R on 2008-05-10
thanks m8 (why everything in linux world is so simple but also so dificult to unterstand???)

---

