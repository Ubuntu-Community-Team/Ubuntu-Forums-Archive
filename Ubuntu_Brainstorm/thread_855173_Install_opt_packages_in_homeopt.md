---
title: "Install opt packages in /home/opt"
date: 2008-07-10
forum: Ubuntu Brainstorm
---

### Post by Afoot on 2008-07-10
I think it would be great if Ubuntu did that, or to /home/apps or whatever the name would be. The big benefit of this would be that if you reinstall Ubuntu (on a separate /home installation), you wouldn't have to reinstall any of those optional packages. Some files could be stored there to remember what dependencies the applications needed too.

---

### Post by mixmaster on 2008-07-10
Presumably you have a separate home partition, which is why you talk about not having to reinstall.  

You can achieve what you want by either:
1. Having a separate /opt partition 
or
2. Creating /home/opt, copying everything from /opt to /home/opt and then deleting /opt and replacing it with a symlink to /home/opt.

(1) is easier if you are doing a new install.
(2) is easier if you have already installed and don't want to muck around with repartitioning.

---

### Post by smartboyathome on 2008-07-10
May I suggest [Rootless Gobolinux]("http://gobo.kundor.org/wiki/Rootless") for you? It allows you to compile programs in your home directory.

---

