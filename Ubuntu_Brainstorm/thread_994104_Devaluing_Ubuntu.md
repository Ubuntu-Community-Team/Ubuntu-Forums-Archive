---
title: "Devaluing Ubuntu"
date: 2008-11-26
forum: Ubuntu Brainstorm
---

### Post by JemW on 2008-11-26
Simple enough question for Ubuntu developers - You are clearly trying to turn Ubuntu into a more 'commercial' operating system, and yet you are *removing / disabling* functionality such as BTNX and leaving 'ordinary' users with multi-function mice out in the cold - unless they are prepared to study cryptic instructions for hours in generally unsuccessful attempts to make *full* use of their mouse!

If any 'ordinary user' can be bothered to install a distro like Arch (and you almost need a degree to do that) - even BTNX just works! Something here does not compute.

What are you going to do to enable people to use their devices easily and intuitively? It's supposed to be getting easier, not harder!

Thanks.

---

### Post by Titan8990 on 2008-11-26
I just had a look and it didn't appear any different than the classic, download program, edit config file, done.

---

### Post by JemW on 2008-11-26
> **Titan8990 said:**
> I just had a look and it didn't appear any different than the classic, download program, edit config file, done.

No. Not quite. Look [here]("http://www.ollisalonen.com/btnx/") at the developers comments. BTNX development has stopped due to fundamental changes in Intrepid. This is well documented with many posts from frustrated users on this forum.

---

### Post by cdenley on 2008-11-26
> **JemW said:**
> No. Not quite. Look [here]("http://www.ollisalonen.com/btnx/") at the developers comments. BTNX development has stopped due to fundamental changes in Intrepid. This is well documented with many posts from frustrated users on this forum.

Well, the developer suspects the problem is with Xorg 7.4, which would mean it isn't Ubuntu-specific. Ubuntu isn't "disabling functionality", they're keeping their software up-to-date. I wouldn't expect them to keep an older version of xorg to prevent regressions which only break software which isn't even in the repos.

The developer doesn't even seem to fully understand why "the kernel input event pipes can no longer be read". Why do you assume this is the result of ubuntu developers intentionally disabling functionality?

---

### Post by bobbocanfly on 2008-11-26
[https://edge.launchpad.net/ubuntu/+filebug](https://edge.launchpad.net/ubuntu/+filebug)

This is something that should be discussed by the developers in a bug report, not with people on a forum. Also, as has been said, as far as I can tell, this is not an Ubuntu specific bug and will affect all Linux distributions. Obviously as I didnt not package these changes, I do not know fully, which is why you should either file a bug report or contact the developers mailing list (ubuntu-devel@lists.ubuntu.com, I think).

---

