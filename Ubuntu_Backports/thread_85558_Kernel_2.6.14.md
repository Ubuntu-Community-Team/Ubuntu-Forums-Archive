---
title: "Kernel 2.6.14"
date: 2005-11-02
forum: Ubuntu Backports
---

### Post by ecobuntu on 2005-11-02
Enough said!

---

### Post by strips on 2005-11-03
[QUOTE=ecobuntu]Enough said![/QUOTE]

Right on!

---

### Post by CAE on 2005-11-03
Kernels will not be backported.

---

### Post by macleod199 on 2005-11-03
[QUOTE=CAE]Kernels will not be backported.[/QUOTE]

Weren't they in the last cycle?

---

### Post by niko_ on 2005-11-03
there is a guide under tips & tricks if you must

---

### Post by matthew on 2005-11-03
[quote=macleod199]Weren't they in the last cycle?[/quote]
No, just security updates.

---

### Post by tseliot on 2005-11-03
[QUOTE=ecobuntu]Enough said![/QUOTE]
Try my guide, it's aimed at newbies (look at the section about vanilla kernels)

[HOWTO: Kernel Compilation for Newbies]("http://www.ubuntuforums.org/showthread.php?t=85064")

---

### Post by SpEcIeS on 2005-11-05
One issue you really need to ask yourself, do you really need that latest kerenel? I mean, if you require a feature that has been implemented then fine, but is it really worth it? I believe that it is always good to stay behind one kernel revision to ensure stability, however I have been swept away with the kernel high. :razz: 

In six months Ubuntu will have 6.04 out and it will have a nice stable kernel. :D

---

### Post by strips on 2005-11-07
For me it's not that i need 2.6.14, but I would like to have a complete system running packages compiled with GCC-4.

I was a kernel maniac a while ago when I ran Gentoo...:rolleyes:

---

### Post by SpEcIeS on 2005-11-07
After replying tp this post I was chatting with Nebetsu regarding kernels, and he, using Debian testing, is currently running 2.6.14. He indicates that it boots faster and performance is a little better. 

Perhaps it is worth the change. ;)

---

### Post by jdong on 2005-11-09
(1) Most 'performance magic' reports with kernel upgrades are myths or psycological effects

(2) Kernel backports are very dangerous stability-wise, not to mention a pain to maintain since a release of Ubuntu would no longer be a uniform platform (harmful for potential Ubuntu-targetted commerical software) and new incompatibilities with existing kernel modules would be pretty painful to deal with.

(3) There is no way that the Backports team would be able to keep up with kernel security and stability updates faster than the Ubuntu Security team! Tracking the kernel is hard work!


As a result, kernel upgrades will not be provided. If you have special circumstances requiring a new kernel, I highly recommend that you do so on your own.

---

### Post by SpEcIeS on 2005-11-09
[QUOTE=jdong](1) Most 'performance magic' reports with kernel upgrades are myths or psycological effects
[/QUOTE]
I really do not totally agree with this statement, but I can definately understand the others. As I am sure that in general this could be true, however I have seen, without negative psychological implications, that some kernels do have performance changes. Nothing extreme, but increases nevertheless.

With that being said, I do believe it is best to just wait until the next version of Ubuntu is out. Really now, six months is not that long. :) March of 2006 is the next due date, right?

---

### Post by jdong on 2005-11-09
Correct -- wait for the next release for kernel updates. 6.04 is the next release (Dapper Drake), due out April 06.

---

### Post by Heretic09 on 2005-11-13
Dunno about that. The kernel-of-the-day maintainers for suse have done a great job in allowing users to update their kernels with a simple apt-get command. One of the few things I miss.

---

### Post by jdong on 2005-11-14
Yes, I've seen plenty a KOTD not completely work, not to mention weird performance for many of them.

Also, note that the SuSE **kernel team** is releasing these KOTD's. They are EXPERTS in kernel maintenance. Note that some average 3rd party packager (like Packman) is not doing this packaging. If you can convince fabbione and whoever else to do it, by all means we'd all be interested! I am not qualified to maintain kernels, and **will NOT pretend to be better than our kernel team!**

---

### Post by samdude9 on 2005-11-19
ive installed it...
its slow...
its rickety...
and not worth the time:mad:

---

### Post by veloct on 2005-11-19
Dapper has packages for 2.6.15 right now so chances are we'll see 2.6.15 or higher with Dapper.  FUN :)

---

