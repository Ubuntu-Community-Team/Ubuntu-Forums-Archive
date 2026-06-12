---
title: "Hardware error in VirtualBox (Existing Vista partition)"
date: 2009-01-11
forum: Virtualisation
---

### Post by wrichtmyer on 2009-01-11
[B]Hello everyone,

Through some trial and error, I have tried to boot my existing Vista partition using VirtualBox. I have gotten it to get to the Windows part of the boot (bypassing Error 17 in the Grub), and then I come upon a hardware error:[/B]


[IMG]http://i90.photobucket.com/albums/k255/wrichtmyer/Error.gif[/IMG]

**Help would be greatly appreciated! :D**

---

### Post by wrichtmyer on 2009-01-11
If it's any help, I also cannot tick the VT-x/AMD-V setting in VirtualBox, and this may have to do with the problem.

---

### Post by wrichtmyer on 2009-01-11
I still need help with this problem.

---

### Post by canabal on 2009-01-11
2 things to try,
1. ensure the windows partition is not mounted in ubuntu when you are trying to run it.
2. run a chkdsk /r

---

