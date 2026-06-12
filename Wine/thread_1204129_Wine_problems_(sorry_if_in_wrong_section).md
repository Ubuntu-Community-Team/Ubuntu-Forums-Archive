---
title: "Wine problems (sorry if in wrong section)"
date: 2009-07-04
forum: Wine
---

### Post by chriscooke109 on 2009-07-04
I recently installed the latest version of wine and added the correct information to the repositories to upgrade this version whenever needed (I just followed the winehq directions so what I just said may be mis-worded).  The first ubuntu update manager broke my wine install, libc6 GLIBC cant be found, i even completely removed and re-installed but still not running a thing not even wine configuration.
Any help with this problem would be greatly appreciated, if you need more more information I will post as advised. Thanks in advance.

---

### Post by kshane on 2009-07-04
Have you tried installing/reinstalling those packages through Synaptic?  I would give that a try...

---

### Post by chriscooke109 on 2009-07-04
I read removing libc6 will stop ubuntu from working so I didn't, I did reinstall though.

The error I get when I type winedbg is:

wine: failed to initialize: /lib32/libc.so.6: version `GLIBC_2.9' not found (required by /usr/lib32/wine/ntdll.dll.so)

---

### Post by donkyhotay on 2009-07-04
FYI this is the correct area for this type of question.

---

### Post by elitenoobboy on 2009-07-06
Try "sudo apt-get install glibc-doc" and that might install what you are missing.

---

### Post by Høvding on 2009-12-09
Hi!

I'm pretty new at working with linux. But I have the same problem:

 wine: failed to initialize: /lib32/libc.so.6: version `GLIBC_2.9' not found (required by /usr/lib32/wine/ntdll.dll.so)

I've tried the solutions offered here and other threads regarding wine failing to initialize. 

I hope someone can help me.

Thanks in advance,
Høvding

---

