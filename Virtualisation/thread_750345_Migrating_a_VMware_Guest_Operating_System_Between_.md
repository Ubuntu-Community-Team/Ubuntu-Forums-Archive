---
title: "Migrating a VMware Guest Operating System Between Machines"
date: 2008-04-09
forum: Virtualisation
---

### Post by GenuineXP on 2008-04-09
I'm wondering if it's possible to migrate a Windows XP installation in VMware on my laptop to my desktop computer. Can this be done with a snapshot, does it require more than that, or is it simply not possible?

The Windows XP installation is using an 8GB virtual hard disk. Could I just copy this virtual hard disk somehow? Also, would Windows be able to handle the sudden hardware change? Obviously, VMware emulates much of the hardware Windows sees, but some of the hardware seems directly available to Windows (such as the CPU).

Thanks!

---

### Post by anaconda on 2008-04-09
Just copy the whole folder, which contains the virtual hard disk.  And dont' have any snapshots those wont propably work..

---

### Post by fjgaude on 2008-04-09
Yep, just copy the whole folder, as annaconda says, to the new machine. What happens is that you might have to re-register Windows if the hardware is different, but that is all.

I've done it many times, even going from an AMD machine to an Intel and it worked.

Try it, you'll like it. <smile>

---

### Post by GenuineXP on 2008-04-09
Should I first create a new equivalent VM on the destination machine, or will VMware just "see" the copied data and display it as a VM?

Thanks for the help.

---

### Post by fjgaude on 2008-04-09
Put the folder where you first installed vmware to see it at. I put mine in my home directory. That is not the default location if you simply hit enter at each prompt when you installed.

---

