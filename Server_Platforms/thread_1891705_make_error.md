---
title: "make error"
date: 2011-12-06
forum: Server Platforms
---

### Post by Fitz_the_gap on 2011-12-06
Hi, has anyone come across this arror before?


cd scstadmin && make all
cd: 1: can't cd to scstadmin
make: *** [all] Error 2

cheers

---

### Post by rubylaser on 2011-12-06
You're going to need to provide more info.  What package are you trying to install, and what steps are you following.  That error is just telling you the make failed because it has nothing to build, because you tried to cd into a directory that doesn't exist the command before.

---

### Post by jaimeaux on 2011-12-06
it looks like you don't have the ability to change dirs into the folder... have you tried just "cd scstadmin?" it could be a permissions issue.

---

### Post by Fitz_the_gap on 2011-12-06
I've just downloaded the package again and it worked looks as though it was a corrupted download. Thanks for the speedy responses!

---

