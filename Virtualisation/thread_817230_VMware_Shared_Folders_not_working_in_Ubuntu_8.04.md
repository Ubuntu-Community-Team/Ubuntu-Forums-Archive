---
title: "VMware Shared Folders not working in Ubuntu 8.04"
date: 2008-06-03
forum: Virtualisation
---

### Post by onyxtape on 2008-06-03
Hi there,

I've got Ubuntu 8.04 running in a VM created by VMWare Workstation 6 using XP SP2 as host. I enabled Shared Folders and set it to c:\work. However, I don't see anything inside /mnt/hgfs (doesn't matter if I run the VM in Workstation, Player, or Server). I've already installed VMWare tools per the peterc.org instructions on a virgin Ubuntu 8.04 install (and I verify that I can move my mouse between host and guest, plus I've got the correct screen resolution). 

What steps am I missing to enable Shared Folders? I've read hints here and there about 8.04 possibly breaking the Shared Folders feature, but I wanted to check here first before going back to an older Ubuntu.

---

### Post by Mhamed_Lahmar on 2008-07-02
I have the exact same symptoms... could a doctor provide some help... thanks!!!!

---

### Post by Keithel on 2008-07-02
I imagine the problem is that when you installed VMware Tools for 8.04, you failed to notice that the vmhgfs module failed to build properly -- this is the kernel module necessary to provide shared folder support.

To fix this, see my recent post: [http://ubuntuforums.org/showthread.php?t=846691](http://ubuntuforums.org/showthread.php?t=846691)

---

