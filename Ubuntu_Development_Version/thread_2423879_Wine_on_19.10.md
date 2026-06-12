---
title: "Wine on 19.10"
date: 2019-07-30
forum: Ubuntu Development Version
---

### Post by deepblue73 on 2019-07-30
Hi, 

Did anyone managed to install Wine on 19.10?

I am having serious dependency problems when I try to install **libfaudio0** packages.

Thanks...

---

### Post by kc1di on 2019-07-31
You have to remember that 19.10 is still in development and not all functions will work as packages are constantly changing at this point. 
The packages you need may not have been rebuilt for 19.10 as yet.

---

### Post by PaulW2U on 2019-07-31
Is this installing WINE from the repositories or elsewhere? 

The latest WINE release seems to be version 4.12.1 but eoan has version 4.0 so dependency problems may occur if you're not installing everything from the Ubuntu repositories. 

Quoting some some error messages or the full terminal output in [NOPARSE][CODE][/NOPARSE] tags from an attempt to install WINE or libfaudio0 might help someone troubleshoot the problem without trying to install it themselves.

---

### Post by deepblue73 on 2019-08-03
Guys, thanks for taking the time.

I don't know why I haven't tried this before, shame on me... but after your replies I went ahead, installed an older version of wine from Ubuntu repositories. Then upgraded to the latest version from Wine repository. No problems at all.
Thanks for lighting the idea in my head.

---

### Post by ajgreeny on 2019-08-03
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

