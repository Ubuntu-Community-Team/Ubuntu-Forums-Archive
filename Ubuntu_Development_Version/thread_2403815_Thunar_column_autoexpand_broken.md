---
title: "Thunar column autoexpand broken"
date: 2018-10-16
forum: Ubuntu Development Version
---

### Post by rattskjelke on 2018-10-16
Today I installed Xubuntu 18.10 current daily build replacing 18.04 but keeping my home partition.
When I run thunar in *detailed list* view it looks like the *automatically expand column* function doesn't work properly.
It won't make the filename column wide enough. 
I don't know how to determine if this problem is in thunar, xfce, something set in /home/user by 18.04 that breaks 18.10, or something else.

---

### Post by again? on 2018-10-16
Create and test a new user account which will tell you if it's a setting in $HOME.

---

### Post by flocculant on 2018-10-17
[https://bugzilla.xfce.org/show_bug.cgi?id=4801](https://bugzilla.xfce.org/show_bug.cgi?id=4801)

Not sure there is a bug reported on launchpad for it - but the work would get done by Xfce and shown on the bug above anyway.

---

