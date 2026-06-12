---
title: "Live CD problem."
date: 2005-12-27
forum: The Cafe
---

### Post by Frank51 on 2005-12-27
Hi Everyone,

I would like to start this post by first wishing the best in the New Year to all of you. I am brand new to Ubuntu and today received my free cd's in the mail. I would like to learn as much as I can, with the hope of making a transition out of Windows. I received the 5.10 distribution and figured I would try the live CD first. I have an HP pavilion with 384 megs of ram running two monitors. One monitor runs off the regular original connection and the other off of an ATI graphics card. I am also running XP PRO. I loaded the live CD restarted and everything seemed to be going well. When I got to the Ubuntu start up screen it went black and all that was on the screen was a single dash line in the upper left hand corner. Nothing happened after that. Does anybody have an idea of what I might do next to correct this problem. Any information will be greatly appreciated.

Thanks again
Frank:)

---

### Post by aysiu on 2005-12-28
No guarantees this'll work, but have you tried Control-Alt-F1 ```
sudo dpkg-reconfigure xserver-xorg
```?

You could also try typing ```
boot vga=791
``` when you first boot the live CD (instead of just pressing Enter).

---

