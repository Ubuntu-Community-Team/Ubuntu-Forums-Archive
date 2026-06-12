---
title: "Which version of a program?"
date: 2005-04-13
forum: Repositories &amp; Backports
---

### Post by titus on 2005-04-13
Say i have multiple reps in my sources.list, such as mallirat and universe. If there are two different versions of an app which is chosen? The most recent I assume. What if the most recent version is unstable or testing?

Thanks, 

Titus.

---

### Post by Nis on 2005-04-24
[QUOTE=titus]Say i have multiple reps in my sources.list, such as mallirat and universe. If there are two different versions of an app which is chosen? The most recent I assume. What if the most recent version is unstable or testing?

Thanks, 

Titus.[/QUOTE]
 I would suggest pinning ([search ULF](http://ubuntuforums.org/search.php?) for how) marillat to a low priority since things change there so often.  Mixing it in with Ubuntu repos can cause trouble if a library in marillat is upgraded to a version that cause dependency conflicts.  Always go for a version that is hoary or warty (or brezzy if you're brave).

---

