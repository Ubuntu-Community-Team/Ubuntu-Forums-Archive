---
title: "Fixed..."
date: 2012-11-17
forum: System76 Support
---

### Post by IntoFlow on 2012-11-17
Seems as if my new computer's SSD just crapped out. I'm starting the computer and looking through the boot menu. Instead of the P1: M4-CT512 SSD showing, I'm getting this:

Realtek PXE B03 D00

AAAAAAAAAAAAAAARGHHH =(

What to do?

========================================

EDIT: I fixed it. User error. All is well and good.

---

### Post by carl4926 on 2012-11-17
Boot a live cd
What do you see

---

### Post by IntoFlow on 2012-11-17
I ended up fixing it somehow... I went into the boot menu and messed around with it and all of a sudden the 512GB drive that Ubuntu is on popped back up but it wasn't set as the priority boot. Instead, the priority was set to "Realtek PXE B03 D00" which doesn't allow the system to boot up.

Weird.

So far I'm unable to set the 512GB to be the default at startup. I have to manually go into the boot menu and make that happen...

---

### Post by pqwoerituytrueiwoq on 2012-11-18
You should be able to change the boot order/priority in the BIOS

---

### Post by IntoFlow on 2012-11-21
Yup, got the hang of that one. It's simpler than I thought.

---

