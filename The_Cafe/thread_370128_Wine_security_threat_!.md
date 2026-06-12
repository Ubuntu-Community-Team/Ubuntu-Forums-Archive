---
title: "Wine security threat !"
date: 2007-02-25
forum: The Cafe
---

### Post by MaximB on 2007-02-25
I've notice that if you install software with wine it installs files on other partition then your home directory and does NOT ask you for a password
it's o.k when you know what you are installing , but then again... it shouldn't be like this.

what do you think ?

---

### Post by GameManK on 2007-02-25
All wine software is installed in ~/.wine
There is no way it can put files outside your home directory unless you run it with sudo (don't!).

---

