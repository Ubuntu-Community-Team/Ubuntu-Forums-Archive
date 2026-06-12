---
title: "Virtualbox kernel modules problems"
date: 2009-03-24
forum: Virtualisation
---

### Post by Koraq on 2009-03-24
Using google, and searching the forums, I've found out that the open source Virtualbox is much harder to get working that the closed one. To bad, I think.

I tried the following, since there are no package for my kernel version in any repositories I use.

apt-get install virtualbox-ose-source
module-assistant auto-install virtualbox-ose-source
/etc/init.d/vboxdrv start

It fails at the second step, trying to compile the module. 

Anyone know how to debug this? I don't even understand the output I get!

---

### Post by KCG102282 on 2009-03-24
If you post the output we might be able to help.

---

### Post by Koraq on 2009-03-30
I admit I took the easy way out and tried the non-free version, and of course it "just worked". Laugh or cry?

---

