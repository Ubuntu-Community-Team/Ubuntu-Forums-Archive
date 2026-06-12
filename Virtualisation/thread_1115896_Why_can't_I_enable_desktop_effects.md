---
title: "Why can't I enable desktop effects?"
date: 2009-04-04
forum: Virtualisation
---

### Post by Bluehotdog5 on 2009-04-04
I'm running Ubuntu in VirtualBox and When i try to enble the effects a pop up comes up saying "can't enable effects" I'm running in the Gnome desktop environment so I know that isn't the problem.

---

### Post by Perryg on 2009-04-04
> **Bluehotdog5 said:**
> I'm running Ubuntu in VirtualBox and When i try to enble the effects a pop up comes up saying "can't enable effects" I'm running in the Gnome desktop environment so I know that isn't the problem.

I feel your pain.
VBox uses its own video driver and supports VESA only. It has just started supporting OpenGL but (IMH0) that does not work well yet.  I am told that the new release 2.20 is supposed to help, but don't quote me on this it may not happen.

---

