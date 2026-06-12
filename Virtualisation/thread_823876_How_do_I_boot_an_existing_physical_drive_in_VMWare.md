---
title: "How do I boot an existing physical drive in VMWare Workstation?"
date: 2008-06-09
forum: Virtualisation
---

### Post by Onay on 2008-06-09
The title says it all... I see all these guides on how to boot existing drives with virtualbox and vmware server but nothing for workstation.

Is there anyway to boot an existing windows drive (physical) with vmware server?

---

### Post by bmwman on 2008-06-10
That's very easy to do. Basically you're going to create a new virtual machine using you're existing physical one. 

1. Go to FILE - Import and hit next
2. Select Physical computer and hit next
3. Select this local machine and hit next
4. Select the partitions you want to import incase you have more than one and hit next. I normally select only the Windows system partition
5. Destination type - Vmware standalone virtual machine
6. Give it a name like XP Pro or whatever you want and location where to save it
7. Just hit next, next until it finish. 

BTW i'm doing it from Windows because I don't have my Ubuntu booted right now but it should be the same in there too.

---

### Post by CovenStine on 2009-11-20
This solution does not seem to hold true for VMware Workstation 7.  There is no 'import' in the file menu.
Has the verbiage changed?
Thanks!

---

### Post by dcstar on 2009-11-21
> **Onay said:**
> The title says it all... I see all these guides on how to boot existing drives with virtualbox and vmware server but nothing for workstation.

Is there anyway to boot an existing windows drive (physical) with vmware server?

It is basically insane to boot partitions that the host OS assumes it has **exclusive** control of in a VM (which will then also assume it has **exclusive** control of that resource).

Make a copy or convert an OS into a VM, but do not try and use a non-VM partition inside a VM.

---

