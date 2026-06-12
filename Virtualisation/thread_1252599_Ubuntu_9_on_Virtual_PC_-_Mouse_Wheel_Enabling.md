---
title: "Ubuntu 9 on Virtual PC - Mouse Wheel Enabling"
date: 2009-08-29
forum: Virtualisation
---

### Post by zongchao on 2009-08-29
I installed Ubuntu 9 on Virtual PC 2007. My mouse wheel didn't work.

I searched and found a number of discussion threads on this problem. But most of them were focused on the adjustment of [Input Device] section in xorg.conf. But whatever the change I made on this, it didn't help.

Occasionally I saw the real solution in another Linux forum, which is simply adding the following kernel boot parameter into menu.lst and reboot:
psmouse.proto=imps

It works!!!:)

---

### Post by zongchao on 2009-08-29
Forgot to mention, the referenced original URL:
[http://forums.fedoraforum.org/showthread.php?t=100706#post619384](http://forums.fedoraforum.org/showthread.php?t=100706#post619384)

---

