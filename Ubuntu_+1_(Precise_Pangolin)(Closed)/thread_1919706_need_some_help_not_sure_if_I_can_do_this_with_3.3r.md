---
title: "need some help not sure if I can do this with 3.3rc2"
date: 2012-02-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rodercot on 2012-02-03
Hey All,

 I found an imon bug and jarod has the fix and a patch has been created already. I need to patch imon.c but I am running 3.3rc2 from mainline. Is there a way to dwlnd the source from kernel.org and set that as my kernel source for my running kernel which is the same. Then I would only have to patch and build the module instead of building a kernel from source.

 Thanks,

 Dave

---

### Post by xyzzyman on 2012-02-03
I can't help you with building just the module, but you will have to apply the 3 patch files from the mainline ppa. There are not ubuntu patches in them but it does set it up the debian way.

---

### Post by rodercot on 2012-02-03
THX,

 I think I read that in the wiki as well about using those patches. I will dig further.

 regards,

 Dave

---

### Post by rodercot on 2012-02-03
got it all patched actually it was pretty easy to build the module outside of the kernel with the installed mainline debs. I thought it would have been a all day affair - LOL. here is a link to how I did. Thanks to Jarod Wilson for the patch and a couple of the threads on-line for the Makefile creation.

 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/925524/comments/7](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/925524/comments/7)

 rgds,

 Dave

---

