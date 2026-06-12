---
title: "Directory '/var/run/screen' must have mode 777."
date: 2012-04-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Skaperen on 2012-04-15
The subject is the message I get when trying to run screen on Xubuntu 12.04 Beta2 amd64.  Other editions are not tested.  This seems to be a change in the screen program itself.  The packaging should be updated to set this permission (it was not already set), or maybe the 01777 (sticky-bit on) permission (which I set and that works).  I have not evaluated security issues for this, but I could see that as a multi-user system risk.

---

### Post by Gregory Lee on 2012-04-15
Mine is 775.  So you're saying the "screen" program will not work?

---

### Post by Skaperen on 2012-04-16
> **Gregory Lee said:**
> Mine is 775.  So you're saying the "screen" program will not work?
It might work with 775.  It did not work with 755.  I didn't test 775.  Maybe it could work with 755, as earlier versions do just find.  Apparently they have added a new test.  But I used 1777 (sticky-bit on so the semantics is that which is appropriate to /tmp).

---

