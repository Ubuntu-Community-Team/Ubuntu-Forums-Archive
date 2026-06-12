---
title: "what it will do"
date: 2010-01-17
forum: Server Platforms
---

### Post by jimfuture12345 on 2010-01-17
hi , i have this command ,but before using it i need to know what it will do with cccam, becouse iam setting directories?:P
 
 
ln /emu/script/cccam /bin/cccam

---

### Post by ajgreeny on 2010-01-17
This will simply link the file /emu/script/cccam, which I presume is a script file, to the binary executable /bin/cccam.

This is occasionally needed for applications to ensure that certain other actions occur when or before the binary is executed. If you open the /emu/script/cccam in a text editor you may be able to see what is going on.

---

