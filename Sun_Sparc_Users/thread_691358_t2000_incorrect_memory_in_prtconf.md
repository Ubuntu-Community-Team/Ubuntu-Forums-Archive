---
title: "t2000 incorrect memory in prtconf"
date: 2008-02-08
forum: Sun Sparc Users
---

### Post by bgervasi on 2008-02-08
I have ubuntu installed on a T2000.  I am using sparc gutsy image.  The T2000 has 8GB of memory, but when I do a prtconf, it only sees 1GB.

Any ides why this is happening.

Thanks

---

### Post by bgervasi on 2008-02-13
Anyone ???

[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

---

### Post by dendrobates on 2008-02-21
what does 'cat /proc/meminfo'  show?

---

### Post by jbenk on 2008-04-03
How is your memory laid out in the slots?  T2000 machines require a minimum of all eight Rank 0 (R0) slots to be filled with memory DIMMS of equal size, i.e eight 1GB DIMMS, each in an R0 slot, indicated on the outer casing of the machine or in the manual - not labeled on the board itself this way.  See Chapter 6.2.1 of the t2000 manual:  [http://docs.sun.com/source/819-2548-14/6_AddNew.html#50413586_16644]("http://docs.sun.com/source/819-2548-14/6_AddNew.html#50413586_16644")

---

### Post by bgervasi on 2008-07-23
Sorry for the long delay here.  I called sun because we thought that the problem was at the hardware level, but sun says its at the OS level. The showfaults does not show any problems., 

cat /proc/meminfo shows only 1G instead of 8.

Sun called me back they say its ubuntu, even though obp banner shows 1G but SC> showfru shows 1G in each slot.

Let me know what to check next.

---

