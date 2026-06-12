---
title: "What I have to do with broken packages?"
date: 2005-05-10
forum: Repositories &amp; Backports
---

### Post by dbolgheroni on 2005-05-10
Hi,

I'm trying to install latex209-bin, but this package has a broken package (tetex-bin is not installable).

OK, but what if I to install latex209-bin anyway? Should I have to wait some days, "apt-get update" and then try to install it again, or I'm really out of luck and have to install from source or stay without latex209-bin?

Thank you.

---

### Post by Klin'Targ on 2005-05-10
Try installing tetex-bin first. Most likely it will give you a more useful error involving a dependancy problem. The easiest way to solve these types of problems on ubuntu is to comment out all repositories not needed to install the package, then install it again. 

Often times you see these kinds of errors when one repository contains a newer version of a package depended on by what you are trying to install, but that repository doesn't include all of the other dependancies. You get version mismatches, and the install fails. 

If removing unneccessary repositories doesn't work, you can try installing whatever versions of packages tetex-bin wants (either manually or by adding a different repository which has these packages).

---

