---
title: "Virtualbox printing from Windows 7 host problems"
date: 2015-07-06
forum: Virtualisation
---

### Post by waterwheel3 on 2015-07-06
I just installed Windows 7 inside virtualbox on an ubuntu 14.04 host. CUPS is running on ubuntu, printing to my local printer.  Windows doesn't see my printer.

I think it's some type of networking related problem?  I can browse the web, but Windows doesn't see the network printer at all, I cut and pasted the exact address for the printer out of the CUPS admin panel (which I can access from within Windows).  

In addition, it was just working on the same computer but with XP instead of 7.  I actually just deleted XP to move up to Windows 7 and now this :).  However this would seem to suggest that it's not a problem on the Ubuntu end.  

Thanks for any thoughts.

---

### Post by waterwheel3 on 2015-07-09
Any thoughts?  Do I need more details?

---

### Post by howefield on 2015-07-09
If it is a network printer I'd set the networking adapter in your virtualbox settings to use bridged mode.

---

