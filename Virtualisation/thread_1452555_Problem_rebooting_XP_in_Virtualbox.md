---
title: "Problem rebooting XP in Virtualbox"
date: 2010-04-12
forum: Virtualisation
---

### Post by asharpham on 2010-04-12
When I install software on XP in Virtualbox that requires me to reboot, XP hangs at the point "Windows is shutting down" and doesn't complete the reboot. Can i do something to stop this happening?

---

### Post by Perryg on 2010-04-12
I had this problem a while back and found that I could either click the acpi shutdown in the title bar under Machine, or I could disable the sound in the guest settings and it would work properly.  VBox had an issue with this several version back and fixed it, but it appears that it has returned.

---

