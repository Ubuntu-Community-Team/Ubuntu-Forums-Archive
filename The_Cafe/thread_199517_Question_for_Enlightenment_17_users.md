---
title: "Question for Enlightenment 17 users"
date: 2006-06-18
forum: The Cafe
---

### Post by johnc4510 on 2006-06-18
I am interested in installing E17, but the only how to's I could find are older and more for Breezy than for Dapper. I am not interested in compiling from source, but am interested in trying this window manager to see if I like it or not. If any of you folks who have already install E17 on Dapper would be willing to help, I would appreciate it. Thanks

---

### Post by nalmeth on 2006-06-18
[http://www.ubuntuforums.org/showthread.php?t=97199](http://www.ubuntuforums.org/showthread.php?t=97199)

this one worked for me, even though it says its for breezy

---

### Post by johnc4510 on 2006-06-18
Thanks nalmeth, I'll give it a try.

---

### Post by drizek on 2006-06-19
you will get an error a few minutes into it about missing some library. Im not sure which one it is specifically, but it start with a g. Just go into adept and install that(and the -dev version of it too) and it should compile fine.

Also, use this command instead of the one in the thread:

sudo ./easy_e17.sh -i --skip=emotion,eclair,evolume,language,mount

---

