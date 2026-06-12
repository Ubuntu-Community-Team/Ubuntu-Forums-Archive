---
title: "Exclude Kernel"
date: 2006-09-04
forum: Server Platforms
---

### Post by rbrugman on 2006-09-04
Is there a way to force apt to exclude kernel upgrades from the list?  I can't get online with anything higher than 2.6.12-10 for some reason and I want to be sure my kernel stays where it is, but every once and a while I do install security upgrades.  Excluding the kernel would be great.

Thanks,
Robert

---

### Post by Glut on 2006-09-05
You can pin a certain package to prevent it from being changed.
It can get complex, scroll to the bottom of: [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)
google revealed a 'beginners' guide, but I think the above is better:
[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)
*Edit* So you want to pin the linux-image-server package, if that wasn't clear.

---

