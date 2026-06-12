---
title: "install jahshaka"
date: 2009-04-05
forum: Ubuntu Studio
---

### Post by camper365 on 2009-04-05
I was trying to install Jahshaka, but when I download the .deb files from the repository, they tell me that I have unsatisfied dependencies: libboost-filesystem1.33.1

Where do I get this library?

EDIT:
I have libboost-filesystem1.34.1 on my computer, but it still tells me I have unresolved dependencies.

EDIT:
I fixed the libboost issue.
New Problem: the .deb file is complaining that the dependency libopenal0 is not met. But when I go to install it, it tells me that it would break libopenal0a, so it can't install. libopenal0a is a dependency of openlibraries, so if I remove that, I remove openlibraries, which prevents me from installing Jahshaka. How do I make libopenal0 and libopenal0a both on the computer at the same time?

---

### Post by qwerty800 on 2009-04-12
Jahshaka is dead since 2006.

I heard that a new version was about to come out, but the developpers don't even give us a SVN.

It's normal that mos of the dependencies have changed their names (libopenal0 is now libopenal1), but the old deb package (and probably the program too) had been configured to use the old libs...

I sincerely don't know what to do either...

---

