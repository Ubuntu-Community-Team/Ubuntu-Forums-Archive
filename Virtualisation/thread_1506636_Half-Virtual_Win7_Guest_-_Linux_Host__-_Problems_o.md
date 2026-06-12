---
title: "Half-Virtual Win7 Guest - Linux Host  - Problems on shared NTFS partition read"
date: 2010-06-10
forum: Virtualisation
---

### Post by DarknessMonk on 2010-06-10
Well, I've kinda successfully did it. It is great! I have a guest Win7,  reading 2 Physical NTFS partitions. That way, i can successfully and  easily share files between my virtual and my half-virtual partitions.  However, when i, for example, create a folder on my Ubuntu 10.04 on the  NTFS partition (with the Half-Virtual machine on), the  Half-Virtual-Windows doesn't recognize the file (only when rebooting).  The same happens the other way, but for the linux to see it, i need only  to get out of the directory. 
Any thoughts on why this happens?

---

### Post by wcorey on 2010-06-12
That's really cool! How do you have the partitions defined? I don't understand what you mean by half virtual. 

I gather from the virtual image of Win7 you mount an externally defined drive. Is this a native drive on Linux? I don't know that I have an answer for you but what you may want to try is to have an external drive mounted by both Win7 images. Or have an external Win7 machine that is visible and mount one of its shares. Perhaps the answer hinges on what you mean by half virtual.

---

