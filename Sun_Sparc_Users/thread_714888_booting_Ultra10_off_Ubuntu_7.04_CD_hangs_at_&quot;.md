---
title: "booting Ultra10 off Ubuntu 7.04 CD hangs at &quot;Booting Linux&quot;"
date: 2008-03-04
forum: Sun Sparc Users
---

### Post by rokoszr on 2008-03-04
I'm trying to install Ubuntu on a Sun Ultra 10, and I'm booting off an Ubuntu feisty 7.04 installation CD.  I hit enter for a boot install, it gets to "Remapping the kernel.. done." and then hangs at "Booting Linux..." - how can I get past this?  Thanks!

---

### Post by ubu_for_umm on 2008-03-25
Did you try "install ide=nodma" ? That has solved some of my booting problems on suns.

---

### Post by capt_caveman on 2008-03-27
At the silo prompt, try

install video=atyfb:off

---

