---
title: "How audit all files read when startup the system?"
date: 2015-10-13
forum: Security
---

### Post by rockii on 2015-10-13
I want check the system integrity before start my application in embeded system. I want check the system integrity comparing all files MD5 in the system. How I can audit what files are read before my application is launch.

Thanks

---

### Post by TheFu on 2015-10-13
[https://en.wikipedia.org/wiki/COPS_%28software%29](https://en.wikipedia.org/wiki/COPS_%28software%29) - don't know if this is still a viable project. Can't remember hearing about it in many years.  You could write a script that creates sha-256 checksums and stores them for all important  files, then compare those against what is on the system as needed.  It is probably  easier to run it weekly and have a read-only filesystem with the programs the rest of the time.

Of course, if you are this paranoid, running off optical media will really be the best answer.  At this level, you'd want to patch weekly, so all the checksums would change constantly, making it next to impossible to know when something has been altered that shouldn't have been altered.

---

### Post by rockii on 2015-10-14
Thanks, I think that this software isn't need. But your second answerd make me think. I will try compare all filesystem (file by file) checksum and I going to work with the machine (any times), later I going to compare the new cheksums.

A lot of thanks

---

### Post by matt_symes on 2015-10-14
Hi

You never mentioned what your embedded device was or the embedded application so the suggestion below may not be applicable for your use case, however....

What about a readonly root file system with tempfs file systems for files that need to change or a readonly file system that gets copied to memory and run from there (if your not memory constrained that is).

You may not need to check your root file system for compromises or corruption (assuming there is no hardware failure)

Both techniques above are used in some embedded systems.

Kind regards

---

