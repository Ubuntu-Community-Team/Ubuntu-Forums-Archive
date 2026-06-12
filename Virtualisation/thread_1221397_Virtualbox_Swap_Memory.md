---
title: "Virtualbox Swap Memory?"
date: 2009-07-23
forum: Virtualisation
---

### Post by AndThenWhat on 2009-07-23
I am trying to give my Virtualbox guest more memory without hogging all of my host's memory.  Is there a way I can provide extra swap/paging/virtual memory to this guest OS?

---

### Post by aesis05401 on 2009-07-23
> **AndThenWhat said:**
> I am trying to give my Virtualbox guest more memory without hogging all of my host's memory.  Is there a way I can provide extra swap/paging/virtual memory to this guest OS?

What is the guest OS?  If it is linux you should be able to partition your new swap space (or add a new .vdi to the VM for this purpopse).  Then use the swapon command to designate new swap space for use.

Check man swapon or swapon -h for more info.
.
Does this help?

---

### Post by AndThenWhat on 2009-07-23
It is Windows XP Professional. I am trying to install some software and it complains saying 'Program is too big to fit in memory.'

---

### Post by aesis05401 on 2009-07-23
> **AndThenWhat said:**
> It is Windows XP Professional. I am trying to install some software and it complains saying 'Program is too big to fit in memory.'

Control panel/System/Advanced(Tab)/Performance(Settings Button)/Advanced(Tab)/VirtualMemory(Change Button).

If you don't have the space you need, then close the VM, create a new virtual drive through the VirtualBox virtual media manager, attach the new drive to the VM as a secondary drive, start the guest XP VM, point the Virtual Memory Manager at the new drive.

Does this help you out?

---

### Post by AndThenWhat on 2009-07-23
Yes. That is what I ended up googling, but I think the secondary drive will be a good idea.

---

