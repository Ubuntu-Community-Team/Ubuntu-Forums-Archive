---
title: "snap packaging questions"
date: 2016-06-16
forum: Ubuntu Application Development
---

### Post by kornelixgmx.de on 2016-06-16
I have been experimenting with making a snap package for fotoxx, and I want to post some observations and solicit opinions. Likely I have stuff to learn.
 
1. The fotoxx snap package size after installation is 116 MB. The debian package after installation is 11 MB.
 
2. If a library function has a bug fix, security hole patch, or performance upgrade, then all snap packages using this function must be upgraded. If snap becomes widely adopted, it seems that millions of unfixed bugs and open security holes will be created. Developers are not going to track hundreds of programs used by their snaps, and rush to make updates whenever one of them has a patch.

3. Snap packages are insulated against API changes in libraries. That is wonderful. However, source code must be adapted anyway, unless further development stops, so the work needed to compensate the API changes is only delayed.

4. gcc compilation in snapcraft is so fast that I suspect optimization is turned off, in spite of my make file calling for 'O2' optimization.

---

