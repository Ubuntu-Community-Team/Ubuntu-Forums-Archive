---
title: "xen problems"
date: 2006-01-05
forum: Server Platforms
---

### Post by jkarpago on 2006-01-05
Hi:

I installed Xen 3.0 and make the boot configuration but when y click on grub after restart, it loads great just for a seconds but then it gives me the next error:

/lib/modules/2.6.12.6-xen/modules.dep No such file or directory

I read in forum that a solution is to create a modules.dep blank file or copy the modules.dep file that ubuntu creates, I did both thing but none works.

Anyone knows a solution?

---

### Post by heimo on 2006-01-10
I'd try:
```
sudo depmod 2.6.12.6-xen
```
and check that modules.dep file was created.

---

### Post by waster on 2006-02-20
Does this help?

[https://wiki.ubuntu.com/XenVirtualMachine/XenOnUbuntuBreezy](https://wiki.ubuntu.com/XenVirtualMachine/XenOnUbuntuBreezy)

---

