---
title: "VirtualBox question"
date: 2008-05-07
forum: Virtualisation
---

### Post by BlackSwordD2 on 2008-05-07
i know i can install another guest OS from a boot disk, but can i have VB access another OS already on my hard drive? (such as while in Ubuntu accessing XP while both are installed on partitions of the same drive)

---

### Post by sdennie on 2008-05-07
I believe that you can but, it may not work as well as you'd like if you dual boot.  The hardware configuration in VirtualBox will appear significantly different and so it will probably cause XP to make you re-register constantly.

---

### Post by Delever on 2008-05-07
There are three ways:
1. Install XP again inside virtual box. You can access files from it which are shared by Ubuntu. You can share your old XP disk. This is recommended way.
2. At least with vmware, you can boot system from existing partition. Now we need someone who actually tried this to clarify if that partition has to be protected from ubuntu in some way while XP is working loaded from it.
3. I heard you can make clone of your existing partition to use with virtual box.

---

### Post by p_quarles on 2008-05-07
Thread moved to Virtualization.

---

### Post by BlackSwordD2 on 2008-05-07
> **Delever said:**
> There are three ways:
1. Install XP again inside virtual box. You can access files from it which are shared by Ubuntu. You can share your old XP disk. This is recommended way.
2. At least with vmware, you can boot system from existing partition. Now we need someone who actually tried this to clarify if that partition has to be protected from ubuntu in some way while XP is working loaded from it.
3. I heard you can make clone of your existing partition to use with virtual box.

oh, i thought VB just started from scratch with the OS, you can have it access the files as if it were to original OS?

---

### Post by Sand Lee on 2008-05-07
> **vor said:**
> I believe that you can but, it may not work as well as you'd like if you dual boot.  The hardware configuration in VirtualBox will appear significantly different and so it will probably cause XP to make you re-register constantly.

It's definately possible, see this tutorial I wrote up: [Boot an existing XP (Physical HD) install with VirtualBox. ]("http://ubuntuforums.org/showthread.php?t=769883") In the tutorial I show a way that will only need you to activate XP once after booting it from VirtualBox. Switching between booting methods becomes just a matter of copying and pasting files. 

I've gone through that tutorial successfully many times with my Hardy/XP dualboot - it works with SP3.

---

