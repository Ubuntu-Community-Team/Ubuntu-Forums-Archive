---
title: "Dual Booting? Try this!"
date: 2006-11-15
forum: Windows
---

### Post by unbuntu kid on 2006-11-15
Instead of shutting down ubuntu or windows when you want to switch operating systems, simply hibernate them.  The GRUB bootload still allows you to choose which OS you want,  but when you select the OS, it simply comes out of hibernation.  
This is more helpful in Windows, but still works in Ubuntu.

---

### Post by WoodyMahan on 2006-11-15
I like the sound of this.  How do you go about doing it?

---

### Post by drFUNK on 2006-11-15
When I used to dual boot XP and OS X, XP rewrote the MBR when it hibernated.  Needless to say I haven't dual booted since then.  My question is, does XP mess with grub when it hibernates?

---

### Post by Chinkostu on 2006-11-15
I thought it was a pretty dangerous idea because it messes with the MBR. and you've still got windows hibernating in the background. major performance hit.

---

### Post by drFUNK on 2006-11-17
> **Chinkostu said:**
> you've still got windows hibernating in the background. major performance hit.

Hibernation just saves everything currently in the RAM to the hard drive, so there'd be no performance hit whatsoever.  I'm just concerned that XP rewrites the MBR when it hibernates.

---

### Post by linux_kid on 2007-02-17
XP does rewrite the MBR, but on my PC, GRUB still works

---

