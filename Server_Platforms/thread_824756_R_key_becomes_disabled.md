---
title: "R key becomes disabled?"
date: 2008-06-10
forum: Server Platforms
---

### Post by iait on 2008-06-10
I've been having trouble with the R key and sometimes the S key becoming disabled when using the console for more than a few minutes. This will happen even when I ssh into the box. First I thought it was a problem with Server 6, then I did a fresh install of 8.04 (on the same box), and still have the same issue, after a period of time of working at the command line (ssh or console) the R key will become disabled and the computer will beep with each hit of the R key. But if I use caps locks, then hit the R key, it will work, just not the lower R key??? Weird. No gui installed. And will usually happen after working in nano or pico. Logging out and back in will temporary fix it till it stops working again.

Any thoughts?

---

### Post by Titan8990 on 2008-06-10
Because this problem carried over from one install to the other I would lean towards a hardware issue. The keyboard could be faulty or the BIOS might not be properly reading the keystoke. That is a odd problem that I would begin to diagnose by using a different keyboard.

---

### Post by iait on 2008-06-10
I would suspect the keyboard or bios as well if it weren't for the fact that it also happens when in a terminal SSH session from a different computer?

-puzzled

---

### Post by Titan8990 on 2008-06-10
Did you set your keyboard layout correctly during the Ubuntu installation?

---

### Post by iait on 2008-06-10
Yup, correct keyboard layout. I suspect if I did have the wrong layout the problem wouldn't appear after several minutes of normal keyboard operation. But then again it happened in version 6 too... so huh.

Weird huh...

---

### Post by iait on 2008-06-10
Issue resolved....

Issue was related to bind, if you type ```
$ bind reload
``` to reload your DNS, you will lose the use of your R key. hahaha.

So... if using bind9, use ```
$ bind9 restart
```

---

