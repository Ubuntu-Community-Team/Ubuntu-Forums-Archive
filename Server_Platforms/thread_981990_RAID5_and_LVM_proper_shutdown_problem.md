---
title: "RAID5 and LVM proper shutdown problem"
date: 2008-11-14
forum: Server Platforms
---

### Post by mcc666 on 2008-11-14
Hello,

   i found out that during one of the latest stages of shutdown or reboot there an information appears that mdX is busy and won't be closed. After ignoring such a behavior for long time i got into trouble - my raid5 drive has failed (with root partition on it) and even after reassembling it i lost some information (fsck was not able to reconstruct all errors). I'm pretty sure that it was caused by the situation i mentioned. I suspect that it is not working properly because of improper init.d construction. Instead of closing filesystems there is just ro remounting. I would imagine that it should be done in different way ie. vgchange -a n, mdadm -S --scan and then shutdown, but having FS still open for RO i'm not convinced if it is the best solution. Do you have any better idea? In which place would be the best to put these commands?

Many thanks for any help.

MCC

---

### Post by psusi on 2008-11-14
You can't unmount the filesystem because it is in use.  By remounting read only, it causes all changes to be flushed and the filesystem to be marked as clean.

---

### Post by mcc666 on 2008-11-14
> **psusi said:**
> You can't unmount the filesystem because it is in use.  By remounting read only, it causes all changes to be flushed and the filesystem to be marked as clean.

So, how to solve the case then?

MCC

---

### Post by psusi on 2008-11-14
> **mcc666 said:**
> So, how to solve the case then?

MCC

Hrm... maybe you should read what I said again.  That's how it is supposed to work.

---

